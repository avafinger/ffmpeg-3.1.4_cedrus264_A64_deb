# FFmpeg 3.1.4 - A64 platform (Cedrus HW Encoder - CMOS Camera)

FFmpeg version 3.1.4 with built in Cedrus264 HW Encoder for the A64 platform.
This was build on Ubuntu Xenial 16.04


Dependencies
============

	sudo apt-get install libmp3lame-dev libx264-dev libpulse-dev libv4l-dev


Source Code and Instructions
============================

https://github.com/linux-sunxi/libcedrus

https://github.com/uboborov/ffmpeg_h264_H3


How to use it
=============

- Attach your CMOS camera with OV5640 enhanced driver loaded
- Clone the repo: git clone https://github.com/avafinger/ffmpeg-3.1.4_cedrus264_A64_deb.git
- cd ffmpeg-3.1.4_cedrus264_A64_deb
- Install the deb package: sudo dpkg -i ffmpeg-3.1.4_1.0-1_arm64.deb
- type: 

	sudo ffmpeg-3.1.4 -f v4l2 -channel 0 -video_size 640x480 -i /dev/video0 -pix_fmt nv12 -r 30 -qp 15 -c:v cedrus264 indoor_test4_640x480_quality5_20secs.mp4

	or

	sudo ffmpeg-3.1.4 -f v4l2 -channel 0 -video_size 1024x768 -i /dev/video0 -pix_fmt nv12 -c:v cedrus264 test4_1024x768.mp4

- adjust the -qp for quality [0,47]

Play the MP4 file with your preferred application

Sample output: indoor 640x480 with different quality set, 20 seconds video.

There is no problem installing this version over stock version, they can co-exist.

Limitations
===========
 * Read the author's note - POC
 * ~~maximum win size 1024x768, above this you get ION memory issues ~~ maximum 1280x960

output:

	Input #0, video4linux2,v4l2, from '/dev/video0':
	  Duration: N/A, start: 327.786662, bitrate: 110592 kb/s
	    Stream #0:0: Video: rawvideo (I420 / 0x30323449), yuv420p, 640x480, 110592 kb/s, 30 fps, 30 tbr, 1000k tbn, 1000k tbc
	[VDPAU SUNXI] VE version 0x1689 opened.
	[mp4 @ 0x1864470] Using AVStream.codec to pass codec parameters to muxers is deprecated, use AVStream.codecpar instead.
	Output #0, mp4, to 'test4_640x480_5.mp4':
	  Metadata:
	    encoder         : Lavf57.41.100
	    Stream #0:0: Video: h264 (cedrus264) ([33][0][0][0] / 0x0021), nv12, 640x480, q=2-31, 200 kb/s, 30 fps, 15360 tbn, 30 tbc
	    Metadata:
	      encoder         : Lavc57.48.101 cedrus264
	Stream mapping:
	  Stream #0:0 -> #0:0 (rawvideo (native) -> h264 (cedrus264))
	Press [q] to stop, [?] for help
	frame=   16 fps=0.0 q=-0.0 size=     602kB time=00:00:00.50 bitrate=9862.6kbits/s
	frame=   32 fps= 31 q=-0.0 size=    1212kB time=00:00:01.03 bitrate=9607.5kbits/s
	frame=   48 fps= 31 q=-0.0 size=    1820kB time=00:00:01.56 bitrate=9518.1kbits/s
	frame=   64 fps= 31 q=-0.0 size=    2409kB time=00:00:02.10 bitrate=9397.1kbits/s
	frame=   80 fps= 30 q=-0.0 size=    2996kB time=00:00:02.63 bitrate=9320.7kbits/s
	frame=   96 fps= 30 q=-0.0 size=    3594kB time=00:00:03.16 bitrate=9296.8kbits/s
	frame=  112 fps= 30 q=-0.0 size=    4194kB time=00:00:03.70 bitrate=9286.3kbits/s
	frame=  128 fps= 30 q=-0.0 size=    4787kB time=00:00:04.23 bitrate=9263.8kbits/s
	frame=  144 fps= 30 q=-0.0 size=    5374kB time=00:00:04.76 bitrate=9235.7kbits/s
	frame=  159 fps= 30 q=-0.0 size=    5946kB time=00:00:05.26 bitrate=9248.6kbits/s
	frame=  175 fps= 30 q=-0.0 size=    6623kB time=00:00:05.80 bitrate=9354.6kbits/s
	frame=  191 fps= 30 q=-0.0 size=    7328kB time=00:00:06.33 bitrate=9477.9kbits/s
	frame=  207 fps= 30 q=-0.0 size=    8044kB time=00:00:06.86 bitrate=9596.4kbits/s
	frame=  223 fps= 30 q=-0.0 size=    8611kB time=00:00:07.40 bitrate=9532.5kbits/s
	frame=  239 fps= 30 q=-0.0 size=    9146kB time=00:00:07.93 bitrate=9443.6kbits/s
	frame=  255 fps= 30 q=-0.0 size=    9693kB time=00:00:08.46 bitrate=9378.4kbits/s
	frame=  271 fps= 30 q=-0.0 size=   10285kB time=00:00:09.00 bitrate=9361.7kbits/s
	frame=  287 fps= 30 q=-0.0 size=   10923kB time=00:00:09.53 bitrate=9385.8kbits/s
	frame=  302 fps= 30 q=-0.0 size=   11584kB time=00:00:10.03 bitrate=9457.8kbits/s
	frame=  317 fps= 30 q=-0.0 size=   12243kB time=00:00:10.53 bitrate=9521.5kbits/s
	frame=  333 fps= 30 q=-0.0 size=   12902kB time=00:00:11.06 bitrate=9550.6kbits/s
	frame=  349 fps= 30 q=-0.0 size=   13538kB time=00:00:11.60 bitrate=9560.3kbits/s
	frame=  365 fps= 30 q=-0.0 size=   14105kB time=00:00:12.13 bitrate=9523.0kbits/s
	frame=  381 fps= 30 q=-0.0 size=   14648kB time=00:00:12.66 bitrate=9473.3kbits/s
	frame=  397 fps= 30 q=-0.0 size=   15202kB time=00:00:13.20 bitrate=9434.3kbits/s
	frame=  413 fps= 30 q=-0.0 size=   15790kB time=00:00:13.73 bitrate=9419.1kbits/s
	frame=  429 fps= 30 q=-0.0 size=   16422kB time=00:00:14.26 bitrate=9429.7kbits/s
	frame=  445 fps= 30 q=-0.0 size=   17053kB time=00:00:14.80 bitrate=9438.9kbits/s
	frame=  460 fps= 30 q=-0.0 size=   17633kB time=00:00:15.30 bitrate=9440.8kbits/s
	frame=  476 fps= 30 q=-0.0 size=   18262kB time=00:00:15.83 bitrate=9448.4kbits/s
	frame=  492 fps= 30 q=-0.0 size=   18854kB time=00:00:16.36 bitrate=9437.1kbits/s
	frame=  508 fps= 30 q=-0.0 size=   19405kB time=00:00:16.90 bitrate=9406.0kbits/s
	frame=  524 fps= 30 q=-0.0 size=   19964kB time=00:00:17.43 bitrate=9381.3kbits/s
	frame=  539 fps= 30 q=-0.0 size=   20491kB time=00:00:17.93 bitrate=9360.2kbits/s
	frame=  555 fps= 30 q=-0.0 size=   21046kB time=00:00:18.46 bitrate=9336.4kbits/s
	frame=  570 fps= 30 q=-0.0 size=   21560kB time=00:00:18.96 bitrate=9312.1kbits/s
	frame=  586 fps= 30 q=-0.0 size=   22089kB time=00:00:19.50 bitrate=9279.5kbits/s
	frame=  601 fps= 30 q=-0.0 size=   22598kB time=00:00:20.00 bitrate=9256.1kbits/s
	frame=  602 fps= 30 q=-0.0 Lsize=   22635kB time=00:00:20.03 bitrate=9256.0kbits/s
	speed=   1x    
	video:22632kB audio:0kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.014865%


	~/ffmpeg-3.1.4$ sudo ./ffmpeg -f v4l2 -channel 0 -video_size 1280x960 -i /dev/video0 -pix_fmt nv12 -r 25 -qp 22 -c:v cedrus264 s5k4ec_test4_1280x960.mp4

	Output #0, mp4, to 's5k4ec_test4_1280x960.mp4':
	  Metadata:
	    encoder         : Lavf57.41.100
	    Stream #0:0: Video: h264 (cedrus264) ([33][0][0][0] / 0x0021), nv12, 1280x960, q=2-31, 200 kb/s, 25 fps, 12800 tbn, 25 tbc
	    Metadata:
	      encoder         : Lavc57.48.101 cedrus264
	Stream mapping:
	  Stream #0:0 -> #0:0 (rawvideo (native) -> h264 (cedrus264))
	Press [q] to stop, [?] for help
	frame=    5 fps=0.0 q=-0.0 size=     245kB time=00:00:00.16 bitrate=12528.3kbits/s
	frame=  120 fps= 57 q=-0.0 size=    5879kB time=00:00:04.76 bitrate=10117.0kbits/s
	frame=  135 fps= 50 q=-0.0 size=    6599kB time=00:00:05.36 bitrate=10086.0kbits/s
	frame=  173 fps= 50 q=-0.0 size=    8399kB time=00:00:06.88 bitrate=10000.6kbits/s
	frame=  189 fps= 46 q=-0.0 size=    9292kB time=00:00:07.52 bitrate=10122.5kbits/s
	frame=  207 fps= 44 q=-0.0 size=   10298kB time=00:00:08.24 bitrate=10237.4kbits/s
	frame=  219 fps= 42 q=-0.0 size=   10965kB time=00:00:08.72 bitrate=10301.1kbits/s
	frame=  236 fps= 40 q=-0.0 size=   11910kB time=00:00:09.40 bitrate=10379.5kbits/s
	frame=  253 fps= 39 q=-0.0 size=   12857kB time=00:00:10.08 bitrate=10448.8kbits/s
	frame=  269 fps= 38 q=-0.0 size=   13748kB time=00:00:10.72 bitrate=10506.2kbits/s
	frame=  285 fps= 37 q=-0.0 size=   14663kB time=00:00:11.36 bitrate=10573.9kbits/s
	frame=  301 fps= 36 q=-0.0 size=   15595kB time=00:00:12.00 bitrate=10646.1kbits/s
	frame=  317 fps= 35 q=-0.0 size=   16511kB time=00:00:12.64 bitrate=10700.9kbits/s
	frame=  333 fps= 35 q=-0.0 size=   17498kB time=00:00:13.28 bitrate=10793.6kbits/s
	frame=  349 fps= 34 q=-0.0 size=   18490kB time=00:00:13.92 bitrate=10881.4kbits/s
	frame=  365 fps= 33 q=-0.0 size=   19472kB time=00:00:14.56 bitrate=10955.5kbits/s
	frame=  381 fps= 33 q=-0.0 size=   20427kB time=00:00:15.20 bitrate=11008.9kbits/s
	frame=  397 fps= 33 q=-0.0 size=   21396kB time=00:00:15.84 bitrate=11065.2kbits/s
	frame=  412 fps= 32 q=-0.0 size=   22254kB time=00:00:16.44 bitrate=11089.1kbits/s
	frame=  428 fps= 32 q=-0.0 size=   23191kB time=00:00:17.08 bitrate=11123.0kbits/s
	frame=  444 fps= 32 q=-0.0 size=   24121kB time=00:00:17.72 bitrate=11150.9kbits/s
	frame=  460 fps= 31 q=-0.0 size=   24986kB time=00:00:18.36 bitrate=11148.5kbits/s
	frame=  476 fps= 31 q=-0.0 size=   25873kB time=00:00:19.00 bitrate=11155.3kbits/s
	frame=  492 fps= 31 q=-0.0 size=   26787kB time=00:00:19.64 bitrate=11173.0kbits/s
	frame=  508 fps= 31 q=-0.0 size=   27719kB time=00:00:20.28 bitrate=11196.8kbits/s
	frame=  524 fps= 30 q=-0.0 size=   28652kB time=00:00:20.92 bitrate=11219.8kbits/s
	frame=  540 fps= 30 q=-0.0 size=   29589kB time=00:00:21.56 bitrate=11242.5kbits/s
	frame=  556 fps= 30 q=-0.0 size=   30529kB time=00:00:22.20 bitrate=11265.4kbits/s
	frame=  572 fps= 30 q=-0.0 size=   31490kB time=00:00:22.84 bitrate=11294.3kbits/s
	frame=  588 fps= 30 q=-0.0 size=   32457kB time=00:00:23.48 bitrate=11323.9kbits/s
	frame=  604 fps= 30 q=-0.0 size=   33378kB time=00:00:24.12 bitrate=11336.2kbits/s
	frame=  619 fps= 29 q=-0.0 size=   34247kB time=00:00:24.72 bitrate=11349.0kbits/s
	frame=  635 fps= 29 q=-0.0 size=   35188kB time=00:00:25.36 bitrate=11366.8kbits/s
	frame=  651 fps= 29 q=-0.0 size=   36190kB time=00:00:26.00 bitrate=11402.5kbits/s
	frame=  667 fps= 29 q=-0.0 size=   37250kB time=00:00:26.64 bitrate=11454.6kbits/s
	frame=  683 fps= 29 q=-0.0 size=   38140kB time=00:00:27.28 bitrate=11453.2kbits/s
	frame=  697 fps= 29 q=-0.0 size=   38833kB time=00:00:27.84 bitrate=11426.6kbits/s
	frame=  713 fps= 29 q=-0.0 size=   39742kB time=00:00:28.48 bitrate=11431.4kbits/s
	frame=  729 fps= 29 q=-0.0 size=   40562kB time=00:00:29.12 bitrate=11410.7kbits/s
	frame=  745 fps= 29 q=-0.0 size=   41428kB time=00:00:29.76 bitrate=11403.7kbits/s
	frame=  761 fps= 28 q=-0.0 size=   42224kB time=00:00:30.40 bitrate=11378.2kbits/s
	frame=  770 fps= 28 q=-0.0 Lsize=   42652kB time=00:00:30.76 bitrate=11359.1kbits/s dup=608 drop=0 speed=1.13x    
	video:42648kB audio:0kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.009592%

