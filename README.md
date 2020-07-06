# crypto_filter_aosp
# 监控java层的加密算法一个ROM

基于android6.0.1 编译

下载地址:

https://drive.google.com/file/d/19G5IXIiww_b5PcQqqiA6lTO6QvnMtQkS/view?usp=sharing



适用手机型号Nexus 6P

使用办法:

1.手机先刷入twrp

2.下载rom解压，adb push ROM/ /sdcard/TWRP/BACKUPS

3.进入twrp，从备份中恢复,重启手机

4.安装你需要监控的apk(系统自动把最后一次安装的apk添加进去监控的列表 /data/local/tmp/monitor_package),只能同时监控一个

5./data/data/package_name/下面生成APK调用的算法,只有三种(数据均为JSON编码,字段为BASE64编码):

  MessageDigest文件为HASH
  
  Cipher文件为加密算法
  
  Mac
  
  
# example
  
  Cipher:
  
  `CipherTag:{"opmode":"DECRYPT_MODE","key":"rM+FMzVeI0VniavN7xISNKzPhTM1XiNF","Key(Base64)":"rM+FMzVeI0VniavN7xISNKzPhTM1XiNF","algorithm":"DESede","SecureRandom":"SHA1PRNG","provider":"","transformation":"DESede\/ECB\/NoPadding","data":"","Base64Data":"","doFinal":"","Base64Cipher":"","StackTrace":"ZGFsdmlrLnN5c3RlbS5WTVN0YWNrLmdldFRocmVhZFN0YWNrVHJhY2UoKSAtMiA8LSAKamF2YS5sYW5nLlRocmVhZC5nZXRTdGFja1RyYWNlKCkgNTgwIDwtIApqYXZheC5jcnlwdG8uQ2lwaGVyLmRvRmluYWwoKSAxLDc4NiA8LSAKY29tLmJhbmdjbGUuYW5kam5pLkpuaUxpYi5jTCgpIC0yIDwtIApjb20udW5pb25wYXkudGlua2VycGF0Y2gubGliLnVwdXRpbHMuRGVzVXRpbHMuaW50ZXJuYWxDcnlwdCgpIC0xIDwtIApjb20uYmFuZ2NsZS5hbmRqbmkuSm5pTGliLmNMKCkgLTIgPC0gCmNvbS51bmlvbnBheS50aW5rZXJwYXRjaC5saWIudXB1dGlscy5EZXNVdGlscy5lY2JEZWNyeXB0KCkgLTEgPC0gCmNvbS5iYW5nY2xlLmFuZGpuaS5KbmlMaWIuY0woKSAtMiA8LSAKY29tLnVuaW9ucGF5LnRpbmtlcnBhdGNoLmxpYi51cHV0aWxzLlByZWZlcmVuY2VVdGlscy5kZWNQcmVmRGF0YSgpIC0xIDwtIApjb20uYmFuZ2NsZS5hbmRqbmkuSm5pTGliLmNMKCkgLTIgPC0gCmNvbS51bmlvbnBheS50aW5rZXJwYXRjaC5saWIudXB1dGlscy5QcmVmZXJlbmNlVXRpbHMuZGVjcnlwdERhdGEoKSAtMSA8LSAKY29tLmJhbmdjbGUuYW5kam5pLkpuaUxpYi5jTCgpIC0yIDwtIApjb20udW5pb25wYXkudGlua2VycGF0Y2gubGliLnVwdXRpbHMuUHJlZmVyZW5jZVV0aWxzLmdldEluZm9tYXRpb24oKSAtMSA8LSAKY29tLnVuaW9ucGF5LnRpbmtlcnBhdGNoLmxpYi51cHV0aWxzLlByZWZlcmVuY2VVdGlscy5nZXRVaWRJbmZvbWF0aW9uKCkgNjMgPC0gCmNvbS51bmlvbnBheS50aW5rZXJwYXRjaC5saWIudXB1dGlscy5EZXZpY2VJbmZvVXRpbC5nZXRVRElEKCkgNjE2IDwtIApjb20uYmFuZ2NsZS5hbmRqbmkuSm5pTGliLmNMKCkgLTIgPC0gCmNvbS51bmlvbnBheS50aW5rZXJwYXRjaC5saWIuc2VydmVyLm1vZGVsLkRldmljZUluZm8uaW5pdERldmljZUluZm8oKSAtMSA8LSAKY29tLnVuaW9ucGF5LnRpbmtlcnBhdGNoLmxpYi5zZXJ2ZXIudXRpbHMuVmVyc2lvblV0aWxzLjxpbml0PigpIDUyIDwtIApjb20udW5pb25wYXkudGlua2VycGF0Y2gubGliLnNlcnZlci5jbGllbnQuVGlua2VyQ2xpZW50QVBJLmluaXQoKSAxNDAgPC0gCmNvbS51bmlvbnBheS50aW5rZXJwYXRjaC5saWIuc2VydmVyLnJlcG9ydGVyLlJlcG9ydFV0aWxzLjxpbml0PigpIDM5IDwtIApjb20udW5pb25wYXkudGlua2VycGF0Y2gubGliLnNlcnZlci5yZXBvcnRlci5SZXBvcnRVdGlscy5pbml0KCkgMjMgPC0gCmNvbS5iYW5nY2xlLmFuZGpuaS5KbmlMaWIuY1YoKSAtMiA8LSAKY29tLnVuaW9ucGF5LnRpbmtlcnBhdGNoLmxpYi50cHJlcG9ydGVyLlRpbmtlck1hbmFnZXIuaW5zdGFsbFRpbmtlcigpIC0xIDwtIApjb20udW5pb25wYXkudGlua2VycGF0Y2gubGliLlRpbmtlclBhdGNoLmluaXQoKSA4MiA8LSAKY29tLnVuaW9ucGF5LmJhc2UuVVBBcHBsaWNhdGlvbkxpa2UuY2hlY2tIb3RQYXRjaCgpIDMwMiA8LSAKY29tLnVuaW9ucGF5LmJhc2UuVVBBcHBsaWNhdGlvbkxpa2Uub25DcmVhdGUoKSAxMDkgPC0gCmphdmEubGFuZy5yZWZsZWN0Lk1ldGhvZC5pbnZva2UoKSAtMiA8LSAKY29tLnRlbmNlbnQudGlua2VyLmxvYWRlci5hcHAuVGlua2VyQXBwbGljYXRpb24uaW52b2tlQXBwTGlrZU9uQ3JlYXRlKCkgMTg5IDwtIApjb20udGVuY2VudC50aW5rZXIubG9hZGVyLmFwcC5UaW5rZXJBcHBsaWNhdGlvbi5vbkNyZWF0ZSgpIDIwNSA8LSAKYW5kcm9pZC5hcHAuSW5zdHJ1bWVudGF0aW9uLmNhbGxBcHBsaWNhdGlvbk9uQ3JlYXRlKCkgMSwwMTMgPC0gCmFuZHJvaWQuYXBwLkFjdGl2aXR5VGhyZWFkLmhhbmRsZUJpbmRBcHBsaWNhdGlvbigpIDQsNzEyIDwtIApkZS5yb2J2LmFuZHJvaWQueHBvc2VkLlhwb3NlZEJyaWRnZS5pbnZva2VPcmlnaW5hbE1ldGhvZE5hdGl2ZSgpIC0yIDwtIApkZS5yb2J2LmFuZHJvaWQueHBvc2VkLlhwb3NlZEJyaWRnZS5oYW5kbGVIb29rZWRNZXRob2QoKSAzNjAgPC0gCmFuZHJvaWQuYXBwLkFjdGl2aXR5VGhyZWFkLmhhbmRsZUJpbmRBcHBsaWNhdGlvbigpIC0xIDwtIAphbmRyb2lkLmFwcC5BY3Rpdml0eVRocmVhZC4td3JhcDEoKSAtMSA8LSAKYW5kcm9pZC5hcHAuQWN0aXZpdHlUaHJlYWQkSC5oYW5kbGVNZXNzYWdlKCkgMSw0MDUgPC0gCmFuZHJvaWQub3MuSGFuZGxlci5kaXNwYXRjaE1lc3NhZ2UoKSAxMDIgPC0gCmFuZHJvaWQub3MuTG9vcGVyLmxvb3AoKSAxNDggPC0gCmFuZHJvaWQuYXBwLkFjdGl2aXR5VGhyZWFkLm1haW4oKSA1LDQyMiA8LSAKamF2YS5sYW5nLnJlZmxlY3QuTWV0aG9kLmludm9rZSgpIC0yIDwtIApjb20uYW5kcm9pZC5pbnRlcm5hbC5vcy5aeWdvdGVJbml0JE1ldGhvZEFuZEFyZ3NDYWxsZXIucnVuKCkgNzI2IDwtIApjb20uYW5kcm9pZC5pbnRlcm5hbC5vcy5aeWdvdGVJbml0Lm1haW4oKSA2MTYgPC0gCmRlLnJvYnYuYW5kcm9pZC54cG9zZWQuWHBvc2VkQnJpZGdlLm1haW4oKSAxMDc="}`
  
  
  MessageDigest:
  
  `MessageDigestTag:{"Algorithm":"SHA-256","Provider":"AndroidOpenSSL","data":"staffId","Base64Data":"c3RhZmZJZA==","digest":"e8f3205321cb6c5a1fcb5ce7a712724707c0cb8d155ed486427a10f368d81910","StackTrace":"ZGFsdmlrLnN5c3RlbS5WTVN0YWNrLmdldFRocmVhZFN0YWNrVHJhY2UoKSAtMiA8LSAKamF2YS5sYW5nLlRocmVhZC5nZXRTdGFja1RyYWNlKCkgNTgwIDwtIApqYXZhLnNlY3VyaXR5Lk1lc3NhZ2VEaWdlc3QuZGlnZXN0KCkgNDc2IDwtIApjb20uYXNpYWluZm8ueGoubGliLnV0aWxzLnkuPGluaXQ+KCkgOCA8LSAKY29tLmFzaWFpbmZvLnhqLmxpYi51dGlscy55LmEoKSAyMzkgPC0gCmNvbS5hc2lhaW5mby54ai5saWIuYy5iLmEoKSAxNSA8LSAKY29tLmFzaWFpbmZvLnhqLmxpYi5jLmIuYSgpIDMwIDwtIApjb20uYXNpYWluZm8ucWRsbS5iLmEuYSgpIDEgPC0gCmNvbS5hc2lhaW5mby5xZGxtLmIuYS5hKCkgNDI4IDwtIApjb20uYXNpYWluZm8ucWRsbS51aS5zcGxhc2guTGF1bmNoZXJBY3Rpdml0eS5pKCkgMSA8LSAKY29tLmFzaWFpbmZvLnFkbG0udWkuc3BsYXNoLkxhdW5jaGVyQWN0aXZpdHkuaigpIDMgPC0gCmNvbS5hc2lhaW5mby5xZGxtLnVpLnNwbGFzaC5MYXVuY2hlckFjdGl2aXR5Lm9uQ3JlYXRlKCkgOSA8LSAKYW5kcm9pZC5hcHAuQWN0aXZpdHkucGVyZm9ybUNyZWF0ZSgpIDYsMjUxIDwtIAphbmRyb2lkLmFwcC5JbnN0cnVtZW50YXRpb24uY2FsbEFjdGl2aXR5T25DcmVhdGUoKSAxLDEwNyA8LSAKYW5kcm9pZC5hcHAuQWN0aXZpdHlUaHJlYWQucGVyZm9ybUxhdW5jaEFjdGl2aXR5KCkgMiwzNjkgPC0gCmFuZHJvaWQuYXBwLkFjdGl2aXR5VGhyZWFkLmhhbmRsZUxhdW5jaEFjdGl2aXR5KCkgMiw0NzYgPC0gCmFuZHJvaWQuYXBwLkFjdGl2aXR5VGhyZWFkLi13cmFwMTEoKSAtMSA8LSAKYW5kcm9pZC5hcHAuQWN0aXZpdHlUaHJlYWQkSC5oYW5kbGVNZXNzYWdlKCkgMSwzNDQgPC0gCmFuZHJvaWQub3MuSGFuZGxlci5kaXNwYXRjaE1lc3NhZ2UoKSAxMDIgPC0gCmFuZHJvaWQub3MuTG9vcGVyLmxvb3AoKSAxNDggPC0gCmFuZHJvaWQuYXBwLkFjdGl2aXR5VGhyZWFkLm1haW4oKSA1LDQyMiA8LSAKamF2YS5sYW5nLnJlZmxlY3QuTWV0aG9kLmludm9rZSgpIC0yIDwtIApjb20uYW5kcm9pZC5pbnRlcm5hbC5vcy5aeWdvdGVJbml0JE1ldGhvZEFuZEFyZ3NDYWxsZXIucnVuKCkgNzI2IDwtIApjb20uYW5kcm9pZC5pbnRlcm5hbC5vcy5aeWdvdGVJbml0Lm1haW4oKSA2MTYgPC0gCmRlLnJvYnYuYW5kcm9pZC54cG9zZWQuWHBvc2VkQnJpZGdlLm1haW4oKSAxMDc="}
MessageDigestTag:{"Algorithm":"MD5","Provider":"AndroidOpenSSL","data":"ns@3'*DHF7\/==","Base64Data":"bnNAMycqREhGNy89PQ==","digest":"31fb6fd3d44c84fb2df62958a7da31f6","StackTrace":"ZGFsdmlrLnN5c3RlbS5WTVN0YWNrLmdldFRocmVhZFN0YWNrVHJhY2UoKSAtMiA8LSAKamF2YS5sYW5nLlRocmVhZC5nZXRTdGFja1RyYWNlKCkgNTgwIDwtIApqYXZhLnNlY3VyaXR5Lk1lc3NhZ2VEaWdlc3QuZGlnZXN0KCkgNDc2IDwtIApqYXZhLnNlY3VyaXR5Lk1lc3NhZ2VEaWdlc3QuZGlnZXN0KCkgNjAxIDwtIApjb20uYXNpYWluZm8ueGoubGliLnV0aWxzLnUuYigpIDQgPC0gCmNvbS5hc2lhaW5mby54ai5saWIudXRpbHMudS5hKCkgMTUgPC0gCmNvbS5hc2lhaW5mby54ai5saWIuYy5iLmEoKSAxNyA8LSAKY29tLmFzaWFpbmZvLnhqLmxpYi5jLmIuYSgpIDMwIDwtIApjb20uYXNpYWluZm8ucWRsbS5iLmEuYSgpIDEgPC0gCmNvbS5hc2lhaW5mby5xZGxtLmIuYS5hKCkgNDI4IDwtIApjb20uYXNpYWluZm8ucWRsbS51aS5zcGxhc2guTGF1bmNoZXJBY3Rpdml0eS5pKCkgMSA8LSAKY29tLmFzaWFpbmZvLnFkbG0udWkuc3BsYXNoLkxhdW5jaGVyQWN0aXZpdHkuaigpIDMgPC0gCmNvbS5hc2lhaW5mby5xZGxtLnVpLnNwbGFzaC5MYXVuY2hlckFjdGl2aXR5Lm9uQ3JlYXRlKCkgOSA8LSAKYW5kcm9pZC5hcHAuQWN0aXZpdHkucGVyZm9ybUNyZWF0ZSgpIDYsMjUxIDwtIAphbmRyb2lkLmFwcC5JbnN0cnVtZW50YXRpb24uY2FsbEFjdGl2aXR5T25DcmVhdGUoKSAxLDEwNyA8LSAKYW5kcm9pZC5hcHAuQWN0aXZpdHlUaHJlYWQucGVyZm9ybUxhdW5jaEFjdGl2aXR5KCkgMiwzNjkgPC0gCmFuZHJvaWQuYXBwLkFjdGl2aXR5VGhyZWFkLmhhbmRsZUxhdW5jaEFjdGl2aXR5KCkgMiw0NzYgPC0gCmFuZHJvaWQuYXBwLkFjdGl2aXR5VGhyZWFkLi13cmFwMTEoKSAtMSA8LSAKYW5kcm9pZC5hcHAuQWN0aXZpdHlUaHJlYWQkSC5oYW5kbGVNZXNzYWdlKCkgMSwzNDQgPC0gCmFuZHJvaWQub3MuSGFuZGxlci5kaXNwYXRjaE1lc3NhZ2UoKSAxMDIgPC0gCmFuZHJvaWQub3MuTG9vcGVyLmxvb3AoKSAxNDggPC0gCmFuZHJvaWQuYXBwLkFjdGl2aXR5VGhyZWFkLm1haW4oKSA1LDQyMiA8LSAKamF2YS5sYW5nLnJlZmxlY3QuTWV0aG9kLmludm9rZSgpIC0yIDwtIApjb20uYW5kcm9pZC5pbnRlcm5hbC5vcy5aeWdvdGVJbml0JE1ldGhvZEFuZEFyZ3NDYWxsZXIucnVuKCkgNzI2IDwtIApjb20uYW5kcm9pZC5pbnRlcm5hbC5vcy5aeWdvdGVJbml0Lm1haW4oKSA2MTYgPC0gCmRlLnJvYnYuYW5kcm9pZC54cG9zZWQuWHBvc2VkQnJpZGdlLm1haW4oKSAxMDc="}
`
