# 检查防火墙状态
firewall-cmd --state
# 关闭防火墙
systemctl stop firewalld.service
# 关闭开机自启
systemctl disable firewalld.service
