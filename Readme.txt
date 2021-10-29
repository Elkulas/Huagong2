�����ļ�����˵����
1. lib�ļ����������п��ļ�libhcnetsdk.so��libHCCore.so��libssl.so��libcrypto.so�Լ�HCNetSDKCom�ļ��ж���Ҫ���ص������С�

2. HCNetSDKCom�ļ��������libhcnetsdk.so��libhpr.so��libHCCore�ļ�����ִ���ļ�����ͬ��Ŀ¼�����߼���ʧ�ܣ����Ե���NET_DVR_SetSDKInitCfg(enumType���͸�ֵΪ2��lpInBuff��Ӧ�ṹ��NET_DVR_LOCAL_SDK_PATH)�������������·����

3. libcrypto.so��libssl.so�ǿ�Դ�⣬������ļ�����ʧ�ܣ����Ե���NET_DVR_SetSDKInitCfg(enumType���͸�ֵΪ3��lpInBuff��Ӧlibcrypto.so���ڵ�·���ַ���)��NET_DVR_SetSDKInitCfg(enumType���͸�ֵΪ4��lpInBuff��Ӧlibssl.so���ڵ�·���ַ���)ָ������Щ���ļ�����·����

��·�����õ�Javaʾ�����롿
//�����ǿ�ľ���·���������ʵ������޸ģ�ע���·�������з���Ȩ��

//����HCNetSDKCom����	
String strPathCom = "/home/hik/Desktop/JavaDemoLinux/lib";
HCNetSDK.NET_DVR_LOCAL_SDK_PATH struComPath = new HCNetSDK.NET_DVR_LOCAL_SDK_PATH();
System.arraycopy(strPathCom.getBytes(), 0, struComPath.sPath, 0, strPathCom.length());
struComPath.write();
hCNetSDK.NET_DVR_SetSDKInitCfg(2, struComPath.getPointer());

//����libcrypto.so����·��	
HCNetSDK.BYTE_ARRAY ptrByteArrayCrypto = new HCNetSDK.BYTE_ARRAY(256);
String strPathCrypto = "/home/hik/Desktop/JavaDemoLinux/lib/libcrypto.so";		
System.arraycopy(strPathCrypto.getBytes(), 0, ptrByteArrayCrypto.byValue, 0, strPathCrypto.length());
ptrByteArrayCrypto.write();
hCNetSDK.NET_DVR_SetSDKInitCfg(3, ptrByteArrayCrypto.getPointer());

//����libssl.so����·��	
HCNetSDK.BYTE_ARRAY ptrByteArraySsl = new HCNetSDK.BYTE_ARRAY(256);	
String strPathSsl = "/home/hik/Desktop/JavaDemoLinux/lib/libssl.so";	
System.arraycopy(strPathSsl.getBytes(), 0, ptrByteArraySsl.byValue, 0, strPathSsl.length());
ptrByteArraySsl.write();
hCNetSDK.NET_DVR_SetSDKInitCfg(4, ptrByteArraySsl.getPointer());

��·�����õ�C++ʾ�����롿
char cryptoPath[2048] = {0};
sprintf(cryptoPath, "/home/test/Desktop/alarm_demo/libcrypto.so");
NET_DVR_SetSDKInitCfg(NET_SDK_INIT_CFG_LIBEAY_PATH, cryptoPath);

char sslPath[2048] = {0};
sprintf(sslPath, "/home/test/Desktop/alarm_demo/libssl.so");
NET_DVR_SetSDKInitCfg(NET_SDK_INIT_CFG_SSLEAY_PATH, sslPath); 
    
NET_DVR_LOCAL_SDK_PATH struComPath = {0};
sprintf(struComPath.sPath, "/home/test/Desktop/alarm_demo"); //HCNetSDKCom�ļ������ڵ�·��
NET_DVR_SetSDKInitCfg(NET_SDK_INIT_CFG_SDK_PATH, &struComPath);