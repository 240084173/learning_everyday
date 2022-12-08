# FFmpeg: decode_video.c
   FFmpeg: decode\_video.c   

| 

FFmpeg

 |

*   [Main Page](index.html)
*   [Related Pages](pages.html)
*   [Modules](modules.html)
*   [Namespaces](namespaces.html)
*   [Data Structures](annotated.html)
*   [Files](files.html)
*   [Examples](examples.html)
*    ![](search/mag_sel.png)[![](search/close.png)
    ](javascript:searchBox.CloseResultsWindow()) 
    

[•All](javascript:void(0))[Data Structures](javascript:void(0))[Namespaces](javascript:void(0))[Files](javascript:void(0))[Functions](javascript:void(0))[Variables](javascript:void(0))[Typedefs](javascript:void(0))[Enumerations](javascript:void(0))[Enumerator](javascript:void(0))[Macros](javascript:void(0))[Groups](javascript:void(0))[Pages](javascript:void(0))

decode\_video.c

/\*

\* Copyright (c) 2001 Fabrice Bellard

\*

\* Permission is hereby granted, free of charge, to any person obtaining a copy

\* of this software and associated documentation files (the "Software"), to deal

\* in the Software without restriction, including without limitation the rights

\* to use, copy, modify, merge, publish, distribute, sublicense, and/or sell

\* copies of the Software, and to permit persons to whom the Software is

\* furnished to do so, subject to the following conditions:

\*

\* The above copyright notice and this permission notice shall be included in

\* all copies or substantial portions of the Software.

\*

\* THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR

\* IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,

\* FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL

\* THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER

\* LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,

\* OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN

\* THE SOFTWARE.

\*/

/\*\*

\* @file

\* video decoding with libavcodec API example

\*

\* @example decode\_video.c

\*/

#include <stdio.h>

#include <stdlib.h>

#include <string.h>

#include <[libavcodec/avcodec.h](avcodec_8h.html)\>

#define INBUF\_SIZE 4096

static void [pgm\_save](decode__video_8c.html#aea973224783a5595366684c76c0ee06c)(unsigned char \*[buf](avisynth__c_8h.html#a5bc5fa69bee375df074734a2c4858604), int [wrap](aarch64_2neontest_8h.html#afcc3d9d5c7982d75dd9756085f644a01), int xsize, int ysize,

char \*filename)

{

FILE \*f;

int i;

f = fopen(filename,"w");

fprintf(f, "P5\\n%d %d\\n%d\\n", xsize, ysize, 255);

for (i = 0; i < ysize; i++)

fwrite(buf + i \* wrap, 1, xsize, f);

fclose(f);

}

static void [decode](decode__video_8c.html#afb211466e5ff14e81d05689d449533e3)([AVCodecContext](structAVCodecContext.html) \*[dec\_ctx](filtering__audio_8c.html#ac2bf6798f37e95d3d2ff2d44e4ab3c12), [AVFrame](structAVFrame.html) \*[frame](demuxing__decoding_8c.html#ad7d33d579a8d4241a5e643e39287a209), [AVPacket](structAVPacket.html) \*[pkt](demuxing__decoding_8c.html#a3d4c6562f0b27cf0cacbbea5c038c090),

const char \*filename)

{

char [buf](avisynth__c_8h.html#a5bc5fa69bee375df074734a2c4858604)\[1024\];

int ret;

ret = [avcodec\_send\_packet](group__lavc__decoding.html#ga58bc4bf1e0ac59e27362597e467efff3)(dec\_ctx, pkt);

if (ret < 0) {

fprintf(stderr, "Error sending a packet for decoding\\n");

exit(1);

}

while (ret >= 0) {

ret = [avcodec\_receive\_frame](group__lavc__decoding.html#ga11e6542c4e66d3028668788a1a74217c)(dec\_ctx, frame);

if (ret == [AVERROR](group__lavu__error.html#gae4bb6f165973d09584e0ec0f335f69ca)(EAGAIN) || ret == [AVERROR\_EOF](group__lavu__error.html#gab4faa0afdf35076914824200331defff))

return;

else if (ret < 0) {

fprintf(stderr, "Error during decoding\\n");

exit(1);

}

printf("saving frame %3d\\n", dec\_ctx->[frame\_number](structAVCodecContext.html#a9e5a25a530d01c04491216c368a1a04a));

fflush(stdout);

/\* the picture is allocated by the decoder. no need to

free it \*/

[snprintf](snprintf_8h.html#aa367b75c5aed883fef5befbdf04835a4)(buf, sizeof(buf), "%s-%d", filename, dec\_ctx->[frame\_number](structAVCodecContext.html#a9e5a25a530d01c04491216c368a1a04a));

[pgm\_save](decode__video_8c.html#aea973224783a5595366684c76c0ee06c)(frame->[data](structAVFrame.html#a1d0f65014a8d1bf78cec8cbed2304992)\[0\], frame->[linesize](structAVFrame.html#aa52bfc6605f6a3059a0c3226cc0f6567)\[0\],

frame->[width](structAVFrame.html#a1e71ce60cedd5f3b6811714a9f7f9e0a), frame->[height](structAVFrame.html#a3f89733f429c98ba5bc64373fb0a3f13), buf);

}

}

int [main](decode__video_8c.html#a3c04138a5bfe5d72780bb7e82a18e627)(int argc, char \*\*argv)

{

const char \*filename, \*outfilename;

const [AVCodec](structAVCodec.html) \*codec;

[AVCodecParserContext](structAVCodecParserContext.html) \*parser;

[AVCodecContext](structAVCodecContext.html) \*[c](vsrc__mptestsrc_8c.html#a075ab94ec54fff64326db9aed0350ffa)\= [NULL](coverity_8c.html#a070d2ce7b6bb7e5c05602aa8c308d0c4);

FILE \*f;

[AVFrame](structAVFrame.html) \*[frame](demuxing__decoding_8c.html#ad7d33d579a8d4241a5e643e39287a209);

[uint8\_t](audio__convert_8c.html#ae1affc9ca37cfb624959c866a73f83c2) inbuf\[[INBUF\_SIZE](decode__video_8c.html#a6378f14810330164b7fb66f3334b2a27) + [AV\_INPUT\_BUFFER\_PADDING\_SIZE](group__lavc__decoding.html#ga8f5b632a03ce83ac8e025894b1fc307a)\];

[uint8\_t](audio__convert_8c.html#ae1affc9ca37cfb624959c866a73f83c2) \*[data](opengl__enc_8c.html#a35090c370ccd7636420cba1acc908df1);

size\_t data\_size;

int ret;

[AVPacket](structAVPacket.html) \*[pkt](demuxing__decoding_8c.html#a3d4c6562f0b27cf0cacbbea5c038c090);

if (argc <= 2) {

fprintf(stderr, "Usage: %s <input file> <output file>\\n", argv\[0\]);

exit(0);

}

filename = argv\[1\];

outfilename = argv\[2\];

[avcodec\_register\_all](group__lavc__core.html#gaf1a2bb4e7c7611c131bb6212bf0fa639)();

pkt = [av\_packet\_alloc](group__lavc__packet.html#gaaf85aa950695631e0217a16062289b66)();

if (!pkt)

exit(1);

/\* set end of buffer to 0 (this ensures that no overreading happens for damaged MPEG streams) \*/

memset(inbuf + [INBUF\_SIZE](decode__video_8c.html#a6378f14810330164b7fb66f3334b2a27), 0, [AV\_INPUT\_BUFFER\_PADDING\_SIZE](group__lavc__decoding.html#ga8f5b632a03ce83ac8e025894b1fc307a));

/\* find the MPEG-1 video decoder \*/

codec = [avcodec\_find\_decoder](group__lavc__decoding.html#ga19a0ca553277f019dd5b0fec6e1f9dca)([AV\_CODEC\_ID\_MPEG1VIDEO](group__lavc__core.html#ggaadca229ad2c20e060a14fec08a5cc7ceaf019b13f4891b36ae579cd7bc96d1f78));

if (!codec) {

fprintf(stderr, "Codec not found\\n");

exit(1);

}

parser = [av\_parser\_init](group__lavc__parsing.html#ga0dd9af605377fcbb49fffd982672d377)(codec->[id](structAVCodec.html#a01a53d07936f4c7ee280444793b6967b));

if (!parser) {

fprintf(stderr, "parser not found\\n");

exit(1);

}

c = [avcodec\_alloc\_context3](group__lavc__core.html#gae80afec6f26df6607eaacf39b561c315)(codec);

if (!c) {

fprintf(stderr, "Could not allocate video codec context\\n");

exit(1);

}

/\* For some codecs, such as msmpeg4 and mpeg4, width and height

MUST be initialized there because this information is not

available in the bitstream. \*/

/\* open it \*/

if ([avcodec\_open2](group__lavc__core.html#ga11f785a188d7d9df71621001465b0f1d)(c, codec, [NULL](coverity_8c.html#a070d2ce7b6bb7e5c05602aa8c308d0c4)) < 0) {

fprintf(stderr, "Could not open codec\\n");

exit(1);

}

f = fopen(filename, "rb");

if (!f) {

fprintf(stderr, "Could not open %s\\n", filename);

exit(1);

}

frame = [av\_frame\_alloc](group__lavu__frame.html#gac700017c5270c79c1e1befdeeb008b2f)();

if (!frame) {

fprintf(stderr, "Could not allocate video frame\\n");

exit(1);

}

while (!feof(f)) {

/\* read raw data from the input file \*/

data\_size = fread(inbuf, 1, [INBUF\_SIZE](decode__video_8c.html#a6378f14810330164b7fb66f3334b2a27), f);

if (!data\_size)

break;

/\* use the parser to split the data into frames \*/

data = inbuf;

while (data\_size > 0) {

ret = [av\_parser\_parse2](group__lavc__parsing.html#ga691ca0258e91f99297e7726f56d8c247)(parser, c, &pkt->[data](structAVPacket.html#aaf4fe58dfcc7c232c1f2268b539d8367), &pkt->[size](structAVPacket.html#a4d1ea19f63eb107111fd650ca514d1f4),

data, data\_size, [AV\_NOPTS\_VALUE](group__lavu__time.html#ga2eaefe702f95f619ea6f2d08afa01be1), [AV\_NOPTS\_VALUE](group__lavu__time.html#ga2eaefe702f95f619ea6f2d08afa01be1), 0);

if (ret < 0) {

fprintf(stderr, "Error while parsing\\n");

exit(1);

}

data += ret;

data\_size -= ret;

if (pkt->[size](structAVPacket.html#a4d1ea19f63eb107111fd650ca514d1f4))

[decode](decode__video_8c.html#afb211466e5ff14e81d05689d449533e3)(c, frame, pkt, outfilename);

}

}

/\* flush the decoder \*/

[decode](decode__video_8c.html#afb211466e5ff14e81d05689d449533e3)(c, frame, [NULL](coverity_8c.html#a070d2ce7b6bb7e5c05602aa8c308d0c4), outfilename);

fclose(f);

[av\_parser\_close](group__lavc__parsing.html#ga325e84c53b8c0dfcb2d933d126f76dd7)(parser);

[avcodec\_free\_context](group__lavc__core.html#gaf869d0829ed607cec3a4a02a1c7026b3)(&c);

[av\_frame\_free](group__lavu__frame.html#ga979d73f3228814aee56aeca0636e37cc)(&frame);

[av\_packet\_free](group__lavc__packet.html#ga1066464e7cdd1f215df6940db94e5d8e)(&pkt);

return 0;

}

* * *

Generated on Fri Jan 12 2018 01:47:35 for FFmpeg by   [![](doxygen.png)](http://www.doxygen.org/index.html) 1.8.6