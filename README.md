# WebAR 最小示例（手机浏览器扫描标记）

用手机摄像头对准 **Hiro 标记**，网页会在标记上叠加 **视频** 和简单 **半透明盒子**（可改成自己的 3D 模型）。

## 为什么选这个方案

- 不需要装 App，普通 **Safari / Chrome** 打开网页即可（需 **HTTPS**）。
- 不需要后端，静态文件托管即可。
- **GitHub Pages** 免费且自带 HTTPS，适合放演示。

## 使用步骤

1. **打印或另一台设备全屏显示** Hiro 标记图：  
   <https://raw.githubusercontent.com/AR-js-org/AR.js/master/data/images/HIRO.jpg>

2. 本地预览（摄像头在非 HTTPS 下可能被浏览器拦截）：

   ```bash
   npx --yes serve -l 8080
   ```

   浏览器打开 `http://本机IP:8080`，手机与电脑同一 WiFi 时用 `http://电脑IP:8080` 访问；若摄像头仍不可用，请用下面 GitHub Pages。

3. **推到 GitHub 并开 Pages**  
   - 新建仓库，把本目录推上去。  
   - Settings → Pages → Source 选分支（如 `main`）和根目录 `/`。  
   - 几分钟后用 `https://你的用户名.github.io/仓库名/` 访问（路径以你实际仓库名为准）。

4. **换自己的视频**  
   把 `mp4`/`webm` 放进 `assets/`，在 `index.html` 里把 `#arvideo` 的 `src` 改成 `./assets/你的文件.mp4`（同域最省事，也少 CORS 问题）。

5. **换 3D 模型（可选）**  
   在 `<a-marker>` 里可加 `<a-gltf-model src="url 或相对路径">`，需 glTF/glb 文件。

## 文件说明

| 文件        | 说明                    |
| ----------- | ----------------------- |
| `index.html`| AR 场景：标记 + 视频 + 盒子 |

## 进阶（用「任意图片」当标记）

本仓库用的是 AR.js 自带的 **Hiro** 预设。若要 **自定义图案/海报** 做标记，需要走 **图像追踪（NFT）** 流程（生成 `.mind` 等），步骤更多；可参考 [MindAR](https://github.com/hiukim/mind-ar-js) 或 AR.js NFT 文档。

## 许可

示例代码可自由使用；演示视频为 MDN 示例素材，仅作演示。
