# engineering-diagram-assistant

DSH（DeepSeek Harness）的工科读题/求解/绘图插件：发一道工科题（可带图），得到**确定性求解结果**、**与数据一致的图**、以及**可核验的校核**。

## 安装

1. 打开 [Releases](https://github.com/huangjinda28-del/engineering-diagram-assistant/releases) 下载 `engineering-diagram-assistant-0.2.1.tgz`
2. PowerShell：

   ```powershell
   dsh plugin --profile desktop add "$env:USERPROFILE\Downloads\engineering-diagram-assistant-0.2.1.tgz"
   ```

3. 重启 DSH

也提供 `install-0.2.1.bat`，双击即可。

## 要求

- DSH：`@deepseek-ai/dsh-tools >= 0.2.1-rc.3`
- 模型：支持图像输入（插件本身不做 OCR；纯文本模型读不了题图）

## 能力

| 类别 | 题型 |
|---|---|
| 平面静力学 | `planar`、`joint`、`beam`、`system`、`friction`、`friction-contact`、`spatial` |
| 平面运动学 | `planar-mechanism`、`circular-slot-slider`、`composition`、`composition-acceleration` |
| 交流电路 | `ac.network`、`three-phase-star`、`three-phase-delta`、`series-rlc`、`parallel-pfc` |
| 直流 / 暂态 | `dc.resistive-network`、`transient.first-order` |
| 动力学 | `work-energy`、`rotation`、`planar` |
| 绘图 | `diagram.scene` + 7 个专用适配器 |

- 82 个测试、10 条基准
- 工具：`engineering_capabilities` / `engineering_solve` / `engineering_render_diagram`

## 已知限制

- 读图依赖模型视觉；插件不做 OCR。
- 不支持 CCVS / CCCS；动力学只覆盖已列章节。
- 静不定结构返回可行区间，不给唯一解。
- 电源变换等中间步骤的等效电路图需要手绘；引擎保证最终等效与校核。

## License

MIT
