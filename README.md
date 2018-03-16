# miniftp-conf
c++教程网出品的miniftp项目中的配置文件模块

虽然c++教程网现在都打不开了，但是我以前还是学到不少东西的，这是我整理出来的miniftp项目中的配置模块，可以借来用到自己的项目中，使用起来虽然不是特别的便利(相对于网上找的玩具代码)，但是它是把整形，bool，字符串都分开来配置，这样跟清晰

### 使用方法

在tunable.h中定义配置文件的所有key
```c
int tunable_pasv_enable; // bool
unsigned int tunable_listen_port; // int
const char *tunable_listen_address; // string
```

在tunable.c中可以给配置项一个默认的值

```c
int tunable_pasv_enable = 1;
unsigned int tunable_listen_port = 21;
const char *tunable_listen_address;
```

在parseconf.c有三个数组，分别在对应的数组中添加配置文件中的key，和配置项key的地址

```c
// bool型
parseconf_bool_array[] = {
	{ "pasv_enable", &tunable_pasv_enable },
	{ "port_enable", &tunable_port_enable },
	{ NULL, NULL }
};

// 无符号整数
parseconf_uint_array[] = {
	{ "listen_port", &tunable_listen_port },
	{ NULL, NULL }
};

// 字符串类型
parseconf_str_array[] = {
	{ "listen_address", &tunable_listen_address },
	{ NULL, NULL }
};

```
最后是配置项了

```c

pasv_enable=YES
port_enable=YES
listen_port=21

# max_clients=333
max_per_ip=2
accept_timeout=60
connect_timeout=60
idle_session_timeout=300
data_connection_timeout=900
local_umask=077
upload_max_rate=102400
download_max_rate=204800
listen_address=wang


```
