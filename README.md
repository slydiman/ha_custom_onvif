The [ONVIF](https://www.home-assistant.io/integrations/onvif/) integration in `Home Assistant` is very conservative.
It does not work with many cameras because a lot of bugs are not fixed for years.
It is impossible to setup some cameras at all. Some cameras can be added, but sensors do not work.

This integration depends on [onvif-zeep-async==1.0.0](https://github.com/hunterjm/python-onvif-zeep-async) and `onvif-zeep-async` depends on [zeep[async]==4.0.0](https://github.com/mvantellingen/python-zeep).

Zeep 4.0.0 has been released half of year ago. It contains a lot of pull request for many months. I have no idea if my [patch](https://github.com/mvantellingen/python-zeep/pull/1206) will be merged and when.
After that, you need to wait for a new release and it should be integrated into Home Assistant.
Perhaps you need to wait another year. Perhaps this will never happen. Who knows?

I have collected few own patches to `zeep` and `ONVIF integration`.
I have renamed `zeep` and `onvif-zeep-async` modules to avoid conflicts and fixed the `ONVIF integration` to use these modules.

If you need to use `XM` (XiongMai, XMEye, iCSee), `Wansview`, `Wanscam` and many other `ONVIF` cameras, which are not supported yet, with `Home Assistant` `ONVIF integration` right now,
just unpack [ha_custom_onvif.zip](https://github.com/slydiman/ha_custom_onvif/releases/latest) to `config`/`custom_components` folder of your `Home Assistant` and restart it.

I hope one day this will no longer be necessary.

Known bugs: Some Wanscam cameras can be added but still not work because GetStreamUri request fails with unknown reason.

Note: I have inversed the value of the binary_sensor (motion detection) because it is necessary at least for XM cameras.
If you don't need it, just remove the word `not` in the file `binary_sensor.py`, line 50.
