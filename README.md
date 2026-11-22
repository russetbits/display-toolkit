# Display Toolkit

显示相关的几个小工具，纯静态页面，无后端、无外部依赖。

**在线使用：<https://matrikslee.github.io/display-toolkit/>**

## 工具

### [EDID 数据库](https://matrikslee.github.io/display-toolkit/edid/)

27947 条公开 EDID 样本，按品牌 / 接口 / 分辨率 / EDID 版本检索。单条记录给出完整解码：preferred timing、最大支持分辨率、像素时钟、CTA 能力（VIC 列表、色彩格式、音频、HDR）、DisplayID 高刷模式、深色、厂商 VSDB。也可以直接粘贴一段 EDID hex 现场解析。

### [DPCD 速查与解析](https://matrikslee.github.io/display-toolkit/dpcd/)

DPCD 寄存器地址速查（DisplayPort 2.1a）；粘贴 sink 的 DPCD dump 可解析出链路能力，以及 DSC / FEC / MST / panel replay 等支持情况。

### [视频时序计算器](https://matrikslee.github.io/display-toolkit/timing/)

输入 `4K60`、`1080i50`、`VIC 97` 这类简短描述，即得完整时序：pixel clock、H/V 的 active / porch / sync / total、行频与场频。同时判定 HDMI TMDS、HDMI 2.1 FRL、DisplayPort 各档链路是否够用。

## 数据与依据

- EDID 样本：[linuxhw/EDID](https://github.com/linuxhw/EDID) 公开数据集
- 时序：CEA-861（VIC 1–127、193–219）、VESA DMT r1.13、VESA CVT 1.2（含 Reduced Blanking v1/v2/v3）
- 接口能力：HDMI 1.4 / 2.0 TMDS，HDMI 2.1 FRL，DisplayPort RBR / HBR / HBR2 / HBR3 / UHBR10 / UHBR13.5 / UHBR20
- DPCD 字段：DisplayPort 2.1a

## 本地运行

```bash
python3 -m http.server 8899
# 打开 http://127.0.0.1:8899/
```

EDID 页用 `fetch` 加载数据，需要 HTTP 环境；直接双击打开会被浏览器的跨域策略挡住。
