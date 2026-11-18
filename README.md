# 菜品照片精修 / Polish Food Photo

清理菜品照片中的杂物和可见文字，补全被裁切的盘子，并将画面统一为正面居中、相机位于盘面上方约 25° 的餐厅风格拍摄角度。

Clean food photographs by removing clutter and visible text, restoring the full plate, and standardizing the composition to a centered restaurant-style camera angle approximately 25° above the plate plane.

## 主要功能

- 清除纸巾、包装、线缆、手部、杂乱餐具、背景餐盘等无关干扰物。
- 默认清除画面中的文字、数字、Logo、水印、标签、字幕和残留字符痕迹。
- 补全被裁切的盘子、碗具和桌面背景，使整个器皿完整显示并保留自然边距。
- 将菜品统一为正面居中的餐厅风格斜拍角度：相机位于盘面上方约 25°，无左右偏转、无画面倾斜。
- 尽量保持原菜品的食材、分量、摆放、颜色、熟度、装饰、餐具设计、光线和景深不变。
- 输出前检查残留文字、变形盘沿、重复食物、额外餐具、错误透视和第二个盘子等问题。

## 安装方法

在 Codex 中发送下面这句话：

> 请使用 `$skill-installer` 从 `https://github.com/hugoyu18-rgb/polish-food-photo` 仓库根目录安装，并将 Skill 命名为 `polish-food-photo`。

安装完成后，在下一轮对话中即可使用。

## 手动安装

1. 点击本仓库右上方绿色的 `Code` 按钮。
2. 选择 `Download ZIP`。
3. 解压下载的 ZIP 文件。
4. 将解压后的文件夹复制到：

```text
C:\Users\你的用户名\.codex\skills\polish-food-photo
```

5. 确认文件夹根目录中存在 `SKILL.md`。
6. 重新打开 Codex；如果 Skill 没有显示，请重启 Codex。

## 使用方法

向 Codex 上传需要处理的菜品照片，然后发送：

> 使用 `$polish-food-photo` 清理这张菜品照片，并统一为正面居中、相机在盘面上方约 25° 的固定斜拍角度。

也可以补充具体要求，例如：

- 去除画面中的纸巾、包装和无关餐具。
- 清除所有文字、Logo、标签和水印。
- 补全被裁切的盘子，完整显示整个器皿。
- 保持菜品的食材、分量、摆放、颜色和装饰不变。
- 保留原来的拍摄角度，不进行角度统一。
- 保留指定的文字、Logo 或背景物品。

## 默认拍摄角度

- 画面正面居中。
- 相机位于盘面上方约 25°，可接受范围为 24° 至 26°。
- 无左右偏转，无画面旋转。
- 盘子前沿接近水平，并能看到器皿前侧外壁。
- 完整显示盘子或碗具，并留出自然边距。

如果用户明确要求保留原角度或指定其他角度，应优先遵循用户要求。

## 重要说明

当原图与目标角度差异较大时，需要重新构建原图中没有显示的区域，因此无法保证像素级完全一致。本 Skill 会尽量保持菜品身份、食材、数量、相对位置、餐具、光线和背景风格一致。

请只处理你拥有或获准编辑的图片。

## 仓库结构

```text
polish-food-photo/
├─ SKILL.md
└─ agents/
   └─ openai.yaml
```

## License

MIT License
