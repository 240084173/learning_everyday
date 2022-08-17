# C++在图片上画框和写汉字并保存 - Smah - 博客园
```


#include <iostream> #include <ctype.h> #include <ft2build.h> #include FT\_FREETYPE\_H
#include <opencv2/core/core.hpp> #include <opencv2/highgui/highgui.hpp> #include <sys/timeb.h> #include <time.h> #include <fstream> #include <stdlib.h> #include <string\> #include <vector> #include <unistd.h>
using namespace std; // //汉字 // int myputText(cv::Mat img, const char \*text, cv::Point pos, cv::Scalar color); // void myputWChar(cv::Mat img, wchar\_t wc, cv::Point &pos, cv::Scalar color);
/\*时间打印\*/
char\*   log\_Time(void)
{ struct  tm      \*ptm; struct timeb   stTimeb; static  char    szTime\[19\];
    ftime(&stTimeb);
    ptm \= localtime(&stTimeb.time);
    sprintf(szTime, "%02d-%02d %02d:%02d:%02d.%03d",ptm->tm\_mon+1, ptm->tm\_mday, ptm->tm\_hour, ptm->tm\_min, ptm->tm\_sec, stTimeb.millitm);
    szTime\[18\] = 0; return szTime;
} class CvxText { public:
    CvxText(const char\* freeType); virtual ~CvxText(); void getFont(int\* type, cv::Scalar\* size=NULL, bool\* underline=NULL, float\* diaphaneity=NULL); void setFont(int\* type, cv::Scalar\* size=NULL, bool\* underline=NULL, float\* diaphaneity=NULL); void restoreFont(); int putText(cv::Mat& img, char\* text, cv::Point pos); int putText(cv::Mat& img, const wchar\_t\* text, cv::Point pos); int putText(cv::Mat& img, const char\* text, cv::Point pos, cv::Scalar color); int putText(cv::Mat& img, const wchar\_t\* text, cv::Point pos, cv::Scalar color); private:
    CvxText& operator\=(const CvxText&); void putWChar(cv::Mat& img, wchar\_t wc, cv::Point& pos, cv::Scalar color);
    FT\_Library   m\_library;
    FT\_Face      m\_face; int m\_fontType;
    cv::Scalar   m\_fontSize; bool m\_fontUnderline; float m\_fontDiaphaneity;
}; // 打开字库
CvxText::CvxText(const char\* freeType)
{
    assert(freeType != NULL); // 打开字库文件, 创建一个字体
    if(FT\_Init\_FreeType(&m\_library)) throw; if(FT\_New\_Face(m\_library, freeType, 0, &m\_face)) throw; // 设置字体输出参数
 restoreFont(); // 设置C语言的字符集环境
    setlocale(LC\_ALL, "");
} // 释放FreeType资源
CvxText::~CvxText()
{
    FT\_Done\_Face(m\_face);
    FT\_Done\_FreeType(m\_library);
} void CvxText::getFont(int\* type, cv::Scalar\* size, bool\* underline, float\* diaphaneity)
{ if (type) \*type = m\_fontType; if (size) \*size = m\_fontSize; if (underline) \*underline = m\_fontUnderline; if (diaphaneity) \*diaphaneity = m\_fontDiaphaneity;
} void CvxText::setFont(int\* type, cv::Scalar\* size, bool\* underline, float\* diaphaneity)
{ // 参数合法性检查
    if (type) { if(type >= 0) m\_fontType = \*type;
    } if (size) {
        m\_fontSize.val\[0\] = std::fabs(size->val\[0\]);
        m\_fontSize.val\[1\] = std::fabs(size->val\[1\]);
        m\_fontSize.val\[2\] = std::fabs(size->val\[2\]);
        m\_fontSize.val\[3\] = std::fabs(size->val\[3\]);
    } if (underline) {
        m\_fontUnderline \= \*underline;
    } if (diaphaneity) {
        m\_fontDiaphaneity \= \*diaphaneity;
    }
    FT\_Set\_Pixel\_Sizes(m\_face, (int)m\_fontSize.val\[0\], 0);
} // 恢复原始的字体设置
void CvxText::restoreFont()
{
    m\_fontType \= 0;            // 字体类型(不支持)
 m\_fontSize.val\[0\] = 20;      // 字体大小
    m\_fontSize.val\[1\] = 0.5;   // 空白字符大小比例
    m\_fontSize.val\[2\] = 0.1;   // 间隔大小比例
    m\_fontSize.val\[3\] = 0;      // 旋转角度(不支持)
 m\_fontUnderline \= false;   // 下画线(不支持)
 m\_fontDiaphaneity \= 1.0;   // 色彩比例(可产生透明效果) // 设置字符大小
    FT\_Set\_Pixel\_Sizes(m\_face, (int)m\_fontSize.val\[0\], 0);
} // 输出函数(颜色默认为白色)
int CvxText::putText(cv::Mat& img, char\* text, cv::Point pos)
{ return putText(img, text, pos, CV\_RGB(255, 255, 255));
} int CvxText::putText(cv::Mat& img, const wchar\_t\* text, cv::Point pos)
{ return putText(img, text, pos, CV\_RGB(255,255,255));
} int CvxText::putText(cv::Mat& img, const char\* text, cv::Point pos, cv::Scalar color)
{ if (img.data == NULL) return -1; if (text == NULL) return -1; int i; for (i = 0; text\[i\] != '\\0'; ++i) {
        wchar\_t wc \= text\[i\]; // 解析双字节符号
        if(!isascii(wc)) mbtowc(&wc, &text\[i++\], 2); // 输出当前的字符
 putWChar(img, wc, pos, color);
    } return i;
} int CvxText::putText(cv::Mat& img, const wchar\_t\* text, cv::Point pos, cv::Scalar color)
{ if (img.data == NULL) return -1; if (text == NULL) return -1; int i; for(i = 0; text\[i\] != '\\0'; ++i) { // 输出当前的字符
 putWChar(img, text\[i\], pos, color);
    } return i;
} // 输出当前字符, 更新m\_pos位置
void CvxText::putWChar(cv::Mat& img, wchar\_t wc, cv::Point& pos, cv::Scalar color)
{ // 根据unicode生成字体的二值位图
    FT\_UInt glyph\_index = FT\_Get\_Char\_Index(m\_face, wc);
    FT\_Load\_Glyph(m\_face, glyph\_index, FT\_LOAD\_DEFAULT);
    FT\_Render\_Glyph(m\_face\->glyph, FT\_RENDER\_MODE\_MONO);
    FT\_GlyphSlot slot \= m\_face->glyph; // 行列数
    int rows = slot->bitmap.rows; int cols = slot->bitmap.width; for (int i = 0; i < rows; ++i) { for(int j = 0; j < cols; ++j) { int off  = i \* slot->bitmap.pitch + j/8; if (slot->bitmap.buffer\[off\] & (0xC0 >> (j%8))) { int r = pos.y - (rows-1\-i); int c = pos.x + j; if(r >= 0 && r < img.rows && c >= 0 && c < img.cols) {
                    cv::Vec3b pixel \= img.at<cv::Vec3b>(cv::Point(c, r));
                    cv::Scalar scalar \= cv::Scalar(pixel.val\[0\], pixel.val\[1\], pixel.val\[2\]); // 进行色彩融合
                    float p = m\_fontDiaphaneity; for (int k = 0; k < 4; ++k) {
                        scalar.val\[k\] \= scalar.val\[k\]\*(1\-p) + color.val\[k\]\*p;
                    }
                    img.at<cv::Vec3b>(cv::Point(c, r))\[0\] = (unsigned char)(scalar.val\[0\]);
                    img.at<cv::Vec3b>(cv::Point(c, r))\[1\] = (unsigned char)(scalar.val\[1\]);
                    img.at<cv::Vec3b>(cv::Point(c, r))\[2\] = (unsigned char)(scalar.val\[2\]);
                }
            }
        }
    } // 修改下一个字的输出位置
    double space = m\_fontSize.val\[0\]\*m\_fontSize.val\[1\]; double sep   = m\_fontSize.val\[0\]\*m\_fontSize.val\[2\];
    pos.x += (int)((cols? cols: space) + sep);
} static int ToWchar(char\* &src, wchar\_t\* &dest, const char \*locale = "zh\_CN.utf8")
{ if (src == NULL) {
        dest \= NULL; return 0;
    } // 根据环境变量设置locale
 setlocale(LC\_CTYPE, locale); // 得到转化为需要的宽字符大小
    int w\_size = mbstowcs(NULL, src, 0) + 1; // w\_size = 0 说明mbstowcs返回值为-1。即在运行过程中遇到了非法字符(很有可能使locale // 没有设置正确)
    if (w\_size == 0) {
        dest \= NULL; return -1;
    } //wcout << "w\_size" << w\_size << endl;
    dest = new wchar\_t\[w\_size\]; if (!dest) { return -1;
    } int ret = mbstowcs(dest, src, strlen(src)+1); if (ret <= 0) { return -1;
    } return 0;
} int wmain() { //printf("打开图之前\[%s\]\\n", log\_Time()); // create image
 cv::Mat image; //std::cout << "size (empty picture): " << image.size().height << " , "<< image.size().width << std::endl;
 CvxText text("./simhei.ttf"); //指定字体
    cv::Scalar size1{ 40, 0.5, 0.1, 0 }; // (字体大小, 无效的, 字符间距, 无效的 }
    text.setFont(nullptr, &size1, nullptr, 0);
    vector<int\> compression\_params;
    compression\_params.push\_back(CV\_IMWRITE\_JPEG\_QUALITY); //选择jpeg
    compression\_params.push\_back(60); //在这个填入你要的图片质量
 printf("start\[%s\]\\n", log\_Time()); for (int i=0;i<10000;i++)
    { // open image
 cv::Mat image;
        image \= cv::imread("20211103182311\_4.186817.jpg"); if (!image.data) {
            printf("\=========================\\n"); return 0;
        } //printf("打开图之后\[%s\]\\n", log\_Time());
        /\*图片大小\*/
        //std::cout << "size (after reading): " << image.size().height << " , "<< image.size().width << std::endl; //画框
        cv::rectangle( image,cv::Point( 155,693),cv::Point( 349,1073),cv::Scalar(0,0,255),3,1); //字母文字 //cv::putText(image, "HELLO", cv::Point(160, 1065), CV\_FONT\_HERSHEY\_COMPLEX, 1, cv::Scalar(0,0, 255), 2, 1);
        char\* str = (char \*)"WZH";
        wchar\_t \*w\_str;
        ToWchar(str,w\_str);
        text.putText(image, w\_str, cv::Point(160, 1065), cv::Scalar(0, 0, 255)); //cv::waitKey(0); //printf("绘制图之后\[%s\]\\n", log\_Time()); 
        cv::imwrite("output.jpg", image,compression\_params); if (i%1000 == 0)
            printf("第%d张图保存\[%s\]\\n", i,log\_Time());
    }
    printf("end\[%s\]\\n", log\_Time()); return 0;
} int main() { //printf("打开图之前\[%s\]\\n", log\_Time()); // create image
 cv::Mat image; //std::cout << "size (empty picture): " << image.size().height << " , "<< image.size().width << std::endl;
 CvxText text("./simhei.ttf"); //指定字体
    cv::Scalar size1{ 40, 0.5, 0.1, 0 }; // (字体大小, 无效的, 字符间距, 无效的 }
    text.setFont(nullptr, &size1, nullptr, 0);
    vector<int\> compression\_params;
    compression\_params.push\_back(CV\_IMWRITE\_JPEG\_QUALITY); //选择jpeg
    compression\_params.push\_back(60); //在这个填入你要的图片质量
 printf("start\[%s\]\\n", log\_Time());
    pid\_t pid \= fork(); if (pid < 0){
        printf("error\\n"); return 1;
    } else if (pid == 0){ for (int i=1;i<=5000;i++)
        { // open image
 cv::Mat image;
            image \= cv::imread("20211103182311\_4.186817.jpg"); if (!image.data) { return 0;
            }
            cv::rectangle( image,cv::Point( 155,693),cv::Point( 349,1073),cv::Scalar(0,0,255),3,1); char\* str = (char \*)"WZH";
            wchar\_t \*w\_str;
            ToWchar(str,w\_str);
            text.putText(image, w\_str, cv::Point(160, 1065), cv::Scalar(0, 0, 255)); 
            cv::imwrite("output1.jpg", image,compression\_params); if (i%1000 == 0 || i==5000)
                printf("\[son\] 第%d张图保存\[%s\]\\n", i,log\_Time());
        }
    } else { for (int i=1;i<=5000;i++)
        { // open image
 cv::Mat image;
            image \= cv::imread("20211103182311\_4.186818.jpg"); if (!image.data) { return 0;
            }
            cv::rectangle( image,cv::Point( 155,693),cv::Point( 349,1073),cv::Scalar(0,0,255),3,1); char\* str = (char \*)"WZH";
            wchar\_t \*w\_str;
            ToWchar(str,w\_str);
            text.putText(image, w\_str, cv::Point(160, 1065), cv::Scalar(0, 0, 255)); 
            cv::imwrite("output2.jpg", image,compression\_params); if (i%1000 == 0 || i==5000)
                printf("\[fat\] 第%d张图保存\[%s\]\\n", i,log\_Time());
        }
    }
    printf("end\[%s\]\\n", log\_Time()); return 0;
}


```