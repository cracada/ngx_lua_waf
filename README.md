##ngx_lua_waf
������
����https://github.com/loveshell/ngx_lua_waf������д
����ԭ�����д��ڴ�����ȫ�ֱ������ڲ������ʹ����б�����ֵ�����ױ����ǣ�����ᵼ��ĳЩ�����ص����󱻷Ź�����ĳЩ�����������ص�����������д��ԭ����
ͬʱ���޸���ԭ�����е�һЩϸ��bug���������˲������ص��߼�
��ӭ�������ָ����ͬʱ��л@loveshell�����Դ��

ʹ��˵����
�谲װopenresty֮�󷽿�ʹ��
����nginx���õ�·��Ϊ��
/home/work/odp/webserver/conf
openresty��lib��·��Ϊ��
/home/work/odp/webserver/lualib
��waf����ѹ����
/home/work/odp/webserver/lualib
������nginx�����ļ��м��ϣ�
lua_package_path '/home/work/odp/webserver/lualib/waf/?.lua;';
lua_shared_dict limit 50m;
lua_shared_dict iplimit 20m;
init_by_lua_file /home/work/odp/webserver/lualib/waf/wafinit.lua;
access_by_lua_file /home/work/odp/webserver/lualib/waf/wafindex.lua;
���nginx�л���������lua����������lua_package_path�У����Էֺŷָ�·������

���ù���Ŀ¼��
RulePath = "/home/work/odp/webserver/lualib/waf/wafconf"
��Ϊ����·�������·�������·����nginx�����ű�����
֮������nginx��Ч

�����ļ�˵����
wafconfig.lua:
RulePath = "./lualib/waf/wafconf/", -- ƥ�����·��
attacklog = "on", -- �Ƿ�����־
logdir = "./logs/hack/", -- ��־Ŀ¼
UrlDeny = "on", -- �Ƿ���url
CookieMatch = "on", -- �Ƿ���cookie
postMatch = "on", -- �Ƿ���post����
whiteModule = "on", -- �Ƿ���url������
black_fileExt = {"php", "jsp"}, -- �ϴ��ļ���׺���
ipWhitelist = {"127.0.0.1"}, -- ������ip�б�֧��*������
ipBlocklist = {"1.0.0.1"}, -- ������ip�б�֧��*������
CCDeny = "off", -- �Ƿ���cc���������
CCrate = "100/60", -- ip�����ض�urlƵ�ʣ���/�룩
ipCCrate = "600/60", -- ip���ʷ�����Ƶ�ʣ���/�룩

wafconf�е����ع�������Դ���е����ã���ҵ�統ǰ������ƥ��������һ��

��ⷽʽ��
����http://ip:port/xxxx.php?id=../etc/passwd����ʾ403 forbidden��������Ч

����ٴθ�л@loveshell�����waf���룬��һ��Ĵ���˼·����ȫ��Դ������git��waf���룬ֻ������˼·����������lua����Ĺ淶����+bug�޸�+���ֹ���ļ�ǿ��
