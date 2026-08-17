# GeoNames 账号配置指南

## 什么是 GeoNames？

GeoNames 是一个免费的地理命名数据库服务，提供 IP 地址定位、地名查询等功能。

**官网：** https://www.geonames.org/

---

## 为什么需要账号？

DYYY Tweak 使用 GeoNames API 来解析**国外 IP 的属地信息**：

- **国内 IP**：使用高德 API（需要 Web 服务 API Key）
- **国外 IP**：使用 GeoNames API（需要 Geonames 账号）

---

## 如何获取 GeoNames 账号？

### 步骤 1：注册账号

1. 访问 https://www.geonames.org/login
2. 点击 "Register" 或 "Sign up"
3. 填写邮箱、用户名、密码
4. 验证邮箱（点击确认链接）
5. 登录成功

### 步骤 2：获取 Username

登录后，Username 就是你的账号名（在个人资料页面可以看到）。

### 步骤 3：配置到 DYYY

在抖音中：
```
双指长按 → DYYY 设置 → 国外解析账号
输入: 你的 Geonames Username
```

---

## API 限制（免费账号）

| 限制项 | 数值 |
|--------|------|
| 每日查询次数 | 20,000 次 |
| 并发请求 | 1 个 |
| 所需功能 | findNearbyPlaceNameJSON |

**注意：** `ipLookup` 接口可能需要付费账号，国内版 DYYY 主要依赖高德 API。

---

## 免费替代方案

如果不想注册 GeoNames，可以考虑：

1. **只使用高德 API**（国内 IP 已足够）
2. **移除国外 IP 解析功能**（修改代码）
3. **使用其他免费 IP 数据库**（如 ip-api.com）

---

## 常见问题

### Q: 我的账号已注册，但无法使用？
A: 确保：
- 邮箱已验证
- 每天请求不超过 20,000 次
- 不使用 ipLookup 接口（免费账号不支持）

### Q: 国内用户使用这个功能吗？
A: 不需要。国内 IP 由高德 API 处理，GeoNames 仅用于国外 IP。

### Q: 可以不配置吗？
A: 可以。国外 IP 会显示"未知"或降级到基础显示。

---

## 技术细节

GeoNames API 端点：
```
https://secure.geonames.org/getJSON?geonameId={ID}&lang=zh&username={USERNAME}
```

返回数据示例：
```json
{
  "geonames": [{
    "name": "Tokyo",
    "countryName": "Japan",
    "adminName1": "Tokyo",
    "lat": "35.67855",
    "lng": "139.68225"
  }]
}
```
