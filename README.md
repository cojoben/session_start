# session_start
After starting a session_start, if the constructed payload is: PHPSESSID=hi6dfe6j3ebq40s0ajlaer1mq2, error=1, an error message will appear due to the session_start function being unable to handle overly long sessions. The error message will include the path used by the session_start and some information about the current server (the test version here is PHP/5.6.40)
<img width="644" alt="1698041225034" src="https://github.com/cojoben/session_start/assets/85165789/fb046f47-9d33-4dca-8e8a-210e937720b0">
When using the thinkphp framework during system construction, the system information of the server and the path and source code of the current error location will be leaked due to the think exception ErrorException processing mechanism (PHP/7.3.33+thinkphp5.0.24 is used here)
<img width="960" alt="1698041389444" src="https://github.com/cojoben/session_start/assets/85165789/ff3185b5-e4b0-4941-9bb9-ca3e9ee484b8">
<img width="960" alt="1698041518343" src="https://github.com/cojoben/session_start/assets/85165789/7725747a-6337-4904-b118-83edc7a51103">
Currently, both php5.6.40 and php7.3.33 have tested and found this issue
