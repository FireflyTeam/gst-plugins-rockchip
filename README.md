
## About

This is a set of GStreamer plugins about camera for rockchip platform.<br>
Most of them were modified based on upstream existing plugin.

This software has been tested only with kernel after 4.4.
This plugin is based on rkisp1, and the 3A-library since then is camera_engine_rkisp.

## Status

| Elements       | Type  |  Comments  | Origin |
| :----:  | :----:  | :----:  | :----:  |
| rkv4l2src        |    Device Sources  |  rockchip isp camera source  | [v4l2src](https://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good/html/gst-plugins-good-plugins-v4l2src.html) |

## Usage

### rkv4l2src
[Pipeline example](https://github.com/rockchip-linux/rk-rootfs-build/blob/master/overlay-debug/usr/local/bin/test_camera.sh)

Most of the properties are the same as that of v4l2src, below are rockchip extend properties:
* `disable-autoconf` : If false, this plugin will init pad format/selection for isp_subdev/sensor, to make the media pipeline work out-of-box: (default : false)
* `iqf-path` : tuning xml IQ-file, needed by 3A : (default : "/etc/cam_iq.xml")
* `isp-mode` : "0A" to disable 3A, "2A" to enable AWB/AE, ~~"3A" to enable AWB/AE/AF~~ : (default : "false")
* `input-crop` : [Selection-crop](https://01.org/linuxgraphics/gfx-docs/drm/media/uapi/v4l/selection-api-003.html), should be "left"x"top"x"width"x"height": (optional)

> NOTE: DO NOT RELY ON `disable-autoconf=false`!  
> This feature is only used to make debug conveniently.  
> rkv4l2src plugin is not designed as a CamHal. It's more like `v4l2-ctl`, just a simple capture program.  
> Since the use cases are divers, please handle `media-controller` and `pad format/selection` in APP level.
