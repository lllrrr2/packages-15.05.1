darkice说明：

在mt7620这种低配置的mipsel上运行时，默认配置会导致推送的语音流延迟卡顿缺失
，并频繁Buffer overrun!报错日志刷屏。

请修改/etc/darkice.cfg中的input配置:

device = /dev/dsp

sampleRate = 11025

保存配置后运行推送命令即可：
darkice -c /etc/darkice.cfg

