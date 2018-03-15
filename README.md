# 阿里云DNS动态解析
支持多解析记录
## 安装 python sdk, pyaml
```
pip install aliyun-python-sdk-alidns pyaml
```

## 修改配置文件 setting.yaml
```yaml
# 阿里云 Access Key ID
access_key_id: "XXX"

# 阿里云 Access Key Secret
access_key_secret: "XXXXXX"

# 阿里云 一级域名
rc_domain: 'github.com'

# 解析记录
rc_rr_list: ['www','*.git']
```

## Access Key
通过阿里云Access Key管理, 获取access_key_id，access_key_secret。

## 通过阿里云域名管理，添加一条域名解析
修改好你使用的一级域名，添加A记录，对一级域名的解析使用记录值为‘*’，A记录可以为你的二级域名，如 www.github.com, *.git.github.com。记录值随便写 8.8.8.8，因为后面会根据实际的IP进行动态更改。

## crontab 定时运行
```
crontab -e
```
```
# Run at every 10th minute
*/10 * * * * /usr/bin/python /path_to/aliyun_ddns.py /dev/null 1>/dev/null
```

