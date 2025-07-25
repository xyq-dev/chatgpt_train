
# VLESS → Clash.Meta 自动转换需求总结

## ✅ 基本功能要求
- 接收 **1 个或多个 VLESS 链接**
- 自动解析为 **Clash.Meta YAML 配置**
- 支持字段：
  - `uuid`, `server`, `port`, `type=ws`, `path`, `host`, `tls`, `fp`, `alpn`, `sni`

## ✅ 输出内容
- 本地一键下载链接（点击下载 `.yaml` 文件）
- 外链复制格式：
  ```
  https://node.daytool.cn/node/文件名.yaml
  ```
- 不自动展示 YAML 内容，除非用户明确说“展示 YAML 内容”

## ✅ 命名规则
- 文件名格式：
  ```
  clash_<6位随机大小写字母>_<当前日期YYYYMMDD>_<节点数量>.yaml
  ```
- 示例：
  ```
  clash_aB3cXy_20250725_2.yaml
  ```

## ✅ 合并规则
- 默认：**每次生成单独文件**
- 如需合并：用户明确说“**合并这些**”或“**继续合并**”
- 如说“**不需要合并**”，之后链接都单独生成

## ✅ 配置结构模板
- proxies: 节点列表
- proxy-groups:
  - name: 🚀 节点选择
  - type: select
  - proxies: 所有节点名称
- rules:
  - MATCH,🚀 节点选择

## ✅ 可选扩展功能
- 更换 proxy-groups 类型，如：
  - url-test
  - fallback
- 添加 DNS 配置、日志等级配置
- 多 YAML 打包成 zip
- 上传到远程服务器（需提供接口）

## ✅ 快捷关键词指令建议
| 指令 | 含义 |
|------|------|
| 合并这几个 | 多节点合并为 1 个 YAML |
| 不需要合并 / 单独生成 | 每个 YAML 单独生成 |
| 展示 yaml | 输出 YAML 配置内容 |
| 给我下载链接 + 外链 | 默认行为 |
| 生成 zip 包 | 打包多个 YAML 输出 |

