# 行为识别算法模块API
## 配置相关API
### 1. 获取报警间隔时间
#### `GET /api/pose/interval`
说明：以秒为单位，整数
##### 返回示例：
```json
{
	"error": 0，
	"data": {
		"interval": 5
	}
}
```
### 2. 设置报警间隔时间
#### `PUT /api/pose/interval`
##### 请求示例：
```json
{
	"interval": 5
}
```
##### 返回示例（成功）：
```json
{
	"error": 0	
}
```
##### 返回示例（失败）：
```json
{
	"error": 1,
	"message": "设置报警间隔时间失败"
	
}
```
### 3. 获取摄像头算法配置
说明：哪些摄像头应用行为识别算法
#### `GET /api/pose/sensors`
##### 返回示例：
```json
{
	"error": 0，
	"data": [{
		"id": 1,
		"url": "rtsp://username:password@ip:port/channel/1"
	},
	{
		"id": 2,
		"url": "rtsp://username:password@ip:port/channel/1"	
	}]
}
```
说明：
- 初始化数据为一个空的数组
- 数组中的摄像头将应用行为识别算法
- 目前只支持rtsp协议
- id应该是与日海传感器管理的摄像头ID对应
### 4. 保存应用行为识别算法的摄像头
#### `PUT /api/pose/sensors`
##### 请求示例：
```json
[
	{
		"id": 1
		"url": "rtsp://username:password@ip:port/channel/1"
	},
	{
		"id": 2
		"url": "rtsp://username:password@ip:port/channel/1"		
	}
]
```
说明：
- PUT的数据将直接覆盖原有数据
- 请先拼接好RTSP的url
##### 返回示例（成功）：
```json
{
	"error": 0	
}
```
##### 返回示例（失败）：
```json
{
	"error": 1,
	"message": "设置报警间隔时间失败"
}
```
## 报警数据API
