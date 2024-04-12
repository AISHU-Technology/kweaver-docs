# һ��windows ��װ
## 1������hyper-v
�ڿ������-����-�����͹ر�windows���ܴ���
- ��ѡhyper-v��hyper-v�����ߺ�hyper-vƽ̨
- ��ѡ������linux��windows��ϵͳ�������ƽ̨

�������Ժ�������������в鿴���⻯�����Ƿ��ѿ���
## 2��docker��װ
��������ص�ַ���£�https://dockerdocs.cn/docker-for-windows/install/index.html

���غ�ֱ�Ӱ�װ��Ĭ����һ�����ɣ�ֱ����װ��ɡ�������cmd�У�ʹ��docker -v�����ж��Ƿ�װ�ɹ���

��Docker Desktop��docker Engine���޸�docker�ľ������ص�ַ��
```
{
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "debug": false,
  "experimental": false,
  "insecure-registries": [],
  "registry-mirrors": [
    "https://ung2thfc.mirror.aliyuncs.com"
  ]
}
```
����ͨ��docker info����鿴�����Ƿ���Ч
## 3��docker-compose ��װ
Docker Desktop����docker-compose���������ⰲװ
# ����linux ��װ
������centos7Ϊ����
## 1��ʹ�� root Ȩ�޸��� yum ��
```
yum -y update
```
�������Ǳ���ִ�еģ������������������ֲ����ݵ�����Ļ��ͱ���update��

ע�⣺
```
yum -y update���������а�ͬʱҲ���������ϵͳ�ںˣ�
yum -y upgrade��ֻ�������а��������������ϵͳ�ں�
```
## 2��ж�ؾɰ汾�����֮ǰ��װ���Ļ���
```
yum remove docker  docker-common docker-selinux docker-engine
```
## 3����װ��Ҫ�������
yum-util �ṩyum-config-manager���ܣ���������devicemapper��������
```
yum install -y yum-utils device-mapper-persistent-data lvm2
```
## 4������ yum Դ

����һ��yumԴ����������������
```
yum-config-manager --add-repo http://download.docker.com/linux/centos/docker-ce.repo������ֿ⣩

yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo������ֿ⣩
```
## 5��ѡ��docker�汾����װ
��1���鿴���ð汾����Щ
```
yum list docker-ce --showduplicates | sort -r
```
��2��ѡ��һ���汾����װ��yum install docker-ce-�汾��
```
yum -y install docker-ce-18.03.1.ce
#������װ���°汾���ϰ汾�����docker��ȡ�������missing signature key
yum install -y docker-ce
```
��3�������������

�� /etc/docker/daemon.json ��д���������ݣ�����ļ����������½����ļ�����
```
{"registry-mirrors":["https://reg-mirror.qiniu.com/"]}
```
֮��������������
```
$ sudo systemctl daemon-reload
$ sudo systemctl restart docker
```
## 6��docker-compose ��װ 
```
#����docker-compose�ļ�
curl -L https://github.com/docker/compose/releases/download/1.21.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose

#���ļ����Ƶ�/usr/local/bin������������
mv docker-compose /usr/local/bin

#����һ��ִ��Ȩ��
chmod +x /usr/local/bin/docker-compose

#�鿴�Ƿ�װ�ɹ�
docker-compose -version
```
# ����mac ��װ
## 1��docker ��װ
��1��Homebrew  �� Cask �Ѿ�֧�� Docker for Mac����˿��Ժܷ����ʹ�� Homebrew Cask �����а�װ��
```
$ brew install --cask --appdir=/Applications docker

==> Creating Caskroom at /usr/local/Caskroom
==> We'll set permissions properly so we won't need sudo in the future
Password:          # ���� macOS ����
==> Satisfying dependencies
==> Downloading https://download.docker.com/mac/stable/21090/Docker.dmg
######################################################################## 100.0%
==> Verifying checksum for Cask docker
==> Installing Cask docker
==> Moving App 'Docker.app' to '/Applications/Docker.app'.
&#x1f37a;  docker was successfully installed!
```
������ Docker app �󣬵�� Next�����ܻ�ѯ����� macOS ��½���룬�����뼴�ɡ�֮��ᵯ��һ�� Docker ���е���ʾ���ڣ�״̬����Ҳ���и�С�����ͼ�ꡣ

��2�������������

����������� Docker for mac Ӧ��ͼ��-> Perferences...-> Daemon-> Registrymirrors�����б�����д��������ַ���޸����֮�󣬵�� Apply&Restart ��ť��Docker �ͻ�������Ӧ�����õľ����ַ�ˡ�

## 2��docker-compose ��װ
Docker Desktop����docker-compose���������ⰲװ