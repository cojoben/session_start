# session_start
在开启session_start后如果构造payload为：PHPSESSID=hi6dfe6j3ebq40s0ajlaer1mq2,error=1则会因为session_start函数无法处理过长的session而出现报错，报错信息会包含session_start使用的路径和当前服务器的部分信息（此处的测试版本为PHP/5.6.40）
<img width="644" alt="1698041225034" src="https://github.com/cojoben/session_start/assets/85165789/fb046f47-9d33-4dca-8e8a-210e937720b0">
而当系统搭建时使用thinkphp框架时则会因为think\exception\ErrorException处理机制导致会泄漏服务器的系统信息和当前报错位置的路径+源代码（此处使用的是PHP/7.3.33+thinkphp5.0.24）
<img width="960" alt="1698041389444" src="https://github.com/cojoben/session_start/assets/85165789/ff3185b5-e4b0-4941-9bb9-ca3e9ee484b8">
<img width="960" alt="1698041518343" src="https://github.com/cojoben/session_start/assets/85165789/7725747a-6337-4904-b118-83edc7a51103">
目前测试了php5.6.40和php7.3.33均发现此问题
