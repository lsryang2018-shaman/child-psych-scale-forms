# 让二维码在任何网络都能打开

现在旧二维码指向的是 `192.168.x.x`，这是本机当前 Wi-Fi 的局域网地址。别人离开这个 Wi-Fi 后无法访问，这是网络限制，不是二维码损坏。

要让别人用自己的网络也能扫码填写，需要把这些静态文件上传到一个公网 HTTPS 地址：

- `psych_scale_index.html`
- `scale_form.html`
- `snapiv_items.json`
- `conners_parent_items.json`
- 可选：`bpfsc11.html`、`bpfsc11_items.json`

推荐方式：

1. 把 `public_scale_forms` 文件夹上传到 GitHub Pages、医院服务器、腾讯云 COS/阿里云 OSS、Netlify 或 Vercel。
2. 得到公网根地址，例如 `https://your-name.github.io/forms`。
3. 在本目录运行：

```powershell
.\make_public_scale_qr.ps1 -BaseUrl "https://your-name.github.io/forms"
```

运行后会生成：

- `snapiv_public_qr.png`
- `conners_parent_public_qr.png`
- `psych_scale_index_public_qr.png`
- `snapiv_qr_title_card_public.png`

以后分享这些 public 二维码，其他人用自己的网络也能打开。

注意：这些网页不会自动把结果上传到服务器，结果只在填写者手机页面显示。若需要后台收集结果，需要再接入数据库或表单平台。
