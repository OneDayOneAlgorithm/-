



창의설계프로젝트 결과보고서
(졸업실험실습 보고서)



독거노인을 위한 모니터링 시스템








2022년 12월 09일

금오공과대학교 전자공학부 제어및로봇전공

   김형진, 지원섭, 최윤호

지도교수 : 최한고
심사위원 : 이승환  심사위원 : 박화평


 독거노인을 위한 모니터링 시스템

김형진†, 지원섭*, 최윤호*
 최한고**


Monitoring System for Elderly Living Alone
Kim Hyeong-Jin†, Ji Won-Seop*, Choi Yoon-Ho* 
Choi Han-Go**

Abstract
 Currently, Korea's population structure is moving beyond an aging society to an ultra-aged society due to the extension of life expectancy and low birth rate. The elderly in Korea were cared for by their immediate family members, including their children, but now the proportion and number of elderly people living alone are increasing every year due to the universalization of nuclear families. Therefore, in this paper, a monitoring system was established to prevent safety accidents of the elderly living alone at low cost. A motion detection sensor and a camera are installed at the front door to film outdoor clothes, a motion recognition sensor and a fall impact detection sensor are installed on the bed to detect dangerous situations during sleep, and a motion detection sensor is installed in the bathroom to detect dangerous situations in the bathroom. In the event of an abnormal situation, measures can be taken quickly to prevent additional accidents.

요약
 현재 한국은 평균 수명연장과 저출산으로 인하여 한국의 인구 구조는 고령화 사회를 넘어 초고령화 사회로 향하고 있다. 한국의 노인들은 자녀를 포함한 직계가족들의 보살핌을 받고 있었으나 현재는 핵가족화의 보편화로 인하여 독거노인의 비율과 그 수가 매년 증가하는 추세이다. 따라서 본 논문에서는 모니터링 시스템을 구축하여 저렴한 비용으로 독거노인들의 안전사고를 예방하는 방법을 연구하였다. 현관문에는 동작 감지 센서와 카메라를 설치해 외출 옷을 촬영하고 침대에는 동작 인식 센서와 낙하 충격 감지 센서를 설치해 수면 중 위험 상황을 감지하고 화장실에는 동작 감지 센서를 설치해 화장실 내 위험 상황을 감지한다. 이상 상황이 발생하면 추가 사고가 발생하지 않도록 신속하게 조치할 수 있다.
    
핵심주제어 : Senior citizen / Monitoring System / Senser / Bluetooth / Arduino / Raspberry pi / Accident prevention






†김형진(학생), 전자공학부 제어및로봇전공, gudwls9966@naver.com, 010-6229-4199     
* 지원섭(학생), 전자공학부 제어및로봇전공, dnjstjq7286@naver.com, 010-5293-8784     
* 최윤호(학생), 전자공학부 제어및로봇전공, dbsgh6506@naver.com, 010-7130-8860   
** 최한고(교수), 전자공학부 제어및로봇전공, hgchoi@kumoh.ac.kr, 010-3977-4267
   
1. 작품과제 필요성

독거노인에게 발생할 수 있는 문제점은 크게 두 가지이다. 첫 번째로는 실내에서의 낙상사고 혹은 고독사이고 두 번째로는 알츠하이머 환자의 실종 신고이다. 낙상사고의 경우 독거노인의 근력 약화가 주된 문제로 실제로 많은 노인이 집안의 일상적인 화장실 같은 공간에서 많은 사고가 일어나게 된다. 이 때문에 우리는 화장실의 문 쪽에 동작감지 센서를 부착하여 장기간의 출입이 없을 때 알림이 가게 해 위험이 발생할 때 그 충격을 감지해 같이 알람이 갈 수 있는 시스템을 구현할 것이다. 또 많은 노인이 수면 중 건강 이상이 발생할 때 대처를 하지 못해 크고 작은 부상과 고독사까지 일어나는 경우가 발생한다. 이를 대처하기 위해 동작 인식 센서를 이용해 수면 중 문제가 생겼을 경우 알람이 갈 수 있도록 한다. 알츠하이머 환자의 경우 화장실에서의 동작센서처럼 외부와의 출입하는 현관문에 동작센서를 설치해 입 출입을 기록한다. 이때 일정 시간이 지나고 나서도 추가적인 입 출입 기록이 없을 때 알람이 가게 한다. 부가적으로 실종이 일어났을 경우를 대비하여 외출 시 카메라가 작동하게 해 외출 시 복장 상태를 자동으로 찍어 보관하여 실종 시 인상착의를 쉽게 파악할 수 있다.


 2. 설계구성 요소 및 제한 요소

설계 구성요소
설계 제한요소
목표
설정
합성
분석
구현/제작
시험/평가
결과
도출
성능
규격/표준
경제성
미학
신뢰성
안정성/내구성
환경
✔
✔
✔
✔
✔
✔
✔
✔
✔
✔
✔
✔
✔



3. 작품과제 해결 방안 및 과정

3.1 서버
3.1.1 서버 생성 과정
처음에는 서버 없이 직접 연결을 채용하려 했으나 가정 내에선 DHCP 방식의 WIFI 연결이     주로 이루어지므로 항상 고정된 IP주소를 유지하기 힘들고 전문 개발자가 아닌 이상 보안     부분 역시 취약했다. 이에 EC2 서버를 개설하려 했으나 개설 과정이 너무 복잡해 다른        방법을 모색했고 데이터를 외부 접근과 보안이 간편한 Amazon Web Service의 Lightsail         서버를 발견했다. 이에 client와 데이터를 주고받는 역할은 Lightsail 서버에 부여하도록         하였다.
3.1.2 서버 구조
Raspberry Pi 두 개를 사용하여 Sensing의 목표 지역인 화장실, 현관문, 침실에서 나오는        Lightsail 서버로 전송하는 것을 목표로 하는 주 데이터 전송 구조이다.
3.2 Database
DB link를 구축하는 것이 중요한데, Local DB인 Lightsail 서버에 FEDERATED ENGINE을      사용하는 DB를 생성하고 Target DB인 라즈베리파이에는 InnoDB를 사용하는 DB를 생성하여 실시간으로 DB 속 data들이 공유되는 link 방식으로 구축하도록 계획하였다. 

3.3 카카오톡
Client쪽 기능들은 카카오톡을 통해 금오헬스 챗봇과 통신하고 챗봇은 Client의 발화문을 토대로 data 열람이 가능한 웹 서버 url을 전달받는 방식으로 개발하고자 계획하였다. 
3.4 센서
첫째로는 레이더 모듈을 통하여 인체를 감지될 경우 값을 출력하여 아두이노에서 값을 블루투스를 통해 라즈베리파이로 전송을 하며, 현관문에 장착할 센서의 경우에는 카메라를 추가로 장착하여 사진을 찍어 Database에 전송하는 방식으로 추가 구현할 것이다. 충격 감지 센서의 경우 가속도 센서를 이용하여 일정량 이상의 충격 값이 전해질 경우, 마찬가지로 블루투스를 통해 전송하는 방식으로 구현하도록 계획하였다.
3.5 사진 데이터의 문제점과 해결책
3.5.1 문제점
BLOB 형식의 사진 데이터를 저장할 수는 있으나 일반적인 DB를 사용하면 Link로 전달 시 손상이 되거나 과도한 패킷 전달 과부하가 유발되어 Database 유지에 부담이 될 수 있음을 발견했다.
3.5.2 해결방안
고용량 데이터들을 효율적으로 저장하고 저장 위치의 URL도 자동으로 반환이 가능한 Google의 Firebase storage server를 사용하는 방향으로 계획을 수정하였음 기존에는 사진 자체를 BLOB 형식으로 저장한 뒤, EC2 서버에 구축할 웹 페이지 서버에서 바로 보는 방식으로 진행하려고 하였으나 	DB server에 부담을 덜 주는 쪽인 사진의 url을 나열, 사용자가 눌러 열람해보는 방식으로 수정을 하였다. 동작을 요약해보자면 firebase를 통해 사진을 저장하는 동시에 저장된 url을 돌려받고, 이를 라즈베리파이 내의 DB에 저장하면 이 DB와 연결되어있는 Lightsail 서버의 DB에도 자동 업로드가 되는 방식이다.
3.6 동작감지 센서의 문제점과 해결책
3.6.1 문제점
MDR_MICRO_A 레이더 센서를 납땜하는 과정에서 과도한 열 공급으로 인하여       레이더가 망가져 정상적으로 값을 측정하는 것이 힘들어짐
3.6.2 해결방안
레이더 센서를 대체하면서 간단하며 직관적으로 회로를 구상하는 방법을 고안하는 도중 PIR 센서로 구현을 하는 방법을 찾게 되었고, HC-SR501이라는 PIR 센서 모듈을 채택하여 사용하였다.
3.7 아두이노 카메라의 문제점과 해결책
3.7.1 문제점
아두이노 카메라에서 찍은 사진을 전송하는 코드는 Python1을 기반하는 코드였으나 Database의 경우, Python3을 기반으로 작성을 하였기 때문에 호환성의 오류가 발생
3.7.2 해결방안
실제 사용하고 있는 화상 웹캠 모듈을 사용하여 라즈베리파이에 직접 PIR 센서와 웹캠을 연결하여 바로 Database에 넣는 형식으로 변경하였다.
3.8 블루투스 모듈의 문제점과 해결책
3.8.1 문제점
HM-10 모델의 경우 통신속도가 115200으로 지정되어 있기에 이를 9600으로 맞추어 주었으나 호환성의 오류로 인하여 AT command가 정상적으로 작동을 하지 않으며 출력값이 제대로 출력되지 않음
3.8.2 해결방안
HM-10 모델의 경우 통신속도가 115200으로 지정되어 있기에 이를 변경하였음에도 불구하고 호환성 부분에서 오류가 지속해서 발생하였다. 따라서 이를 해결하기 통신속도가 9600으로 설정되어 나오는 HC-06 모델을 사용함으로써 대체하였다.


                                -DB 구조 및 서버 구상안-


                                    -시스템 구성도-
4. 개념설계 및 상세설계
1) DB

DB를 사용할 라즈베리파이에는 다음의 총 세가지 절차가 필요하다.
외부(Firebase) 접근 계정 권한 설정, DB 내의 Table engine 설정 및 table 생성, 그리고 DB      server가 통신할 port의 방화벽 해제하기 이렇게 세 가지 이다. 
방화벽 해제는 라즈베리파이에서 ‘ufw’라는 리눅스 방화벽 프로그램을 사용하여 해제하였고,    아래의 명령어는 같은 리눅스 기반의 우분투에서 예시로 실행하였다.


                           -ufw설치-


ufw를 먼저 설치하고 난 다음, inactive 상태의 ufw를 활성화시켰다.

                        -ufw status 확인 및 활성화-

활성화가 완료되면 명령어를 통해 DB서버에 할당되는 3306번 port를 열어주었다.

             -ufw로 3306포트를 개방-

이렇게 방화벽을 열고 3306번 포트를 열어주면 port방화벽 관련 절차는 끝이 나게 된다.
이 후는 오픈소스인 MariaDB를 설치하여 센서값과 사진의 url을 저장할 data table을           생성하는 절차를 시작한다.

                             -mariaDB설치-
명령어로 MariaDB를 설치하고 난 뒤, conf 파일을 수정하여 DB에 외부IP가 접근 가능할 수    있도록 Bind address를 수정한다.

                     -MariaDB의 bind address 해제-
bind address의 맨 앞에 주석 처리 ‘#’을 붙여주어 127.0.0.1(Local)에만 한정되었던 접근         권한이 해제되고 외부 IP도 접근이 가능하게 된다.

이 후, MariaDB 내에서 mysql을 DB로 지정한 뒤, EC2 서버에 저장될 데이터의 원본이 담길    Table을 생성한다.

CREATE TABLE SLEEP(
ID INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
URL VARCHAR(250) NOT NULL,
DATE DATETIME DEFAULT NOW())
CHARSET=’UTF8’ ENGINE=InnoDB;
 중요한 것은 라즈베리파이에 InnoDB engine을 사용한 테이블을 먼저 만들어주는 것이다. 테이블을 생성하고 난 다음, 이 테이블에 접근할 때 쓰일 DB 내의 계정을 만들어준다.

CREATE USER ‘user_ID’@’%’ IDENTIFIED BY ‘passwd’;

GRANT ALL PRIVILEGES ON mysql.* TO ‘user_ID’@’%’;

FLUSH PRIVILEGES;

이는 Lightsail 서버에 있는 원격지 DB 뿐 아니라 라즈베리파이 내의 python 실행 파일을       통해 db에 값을 저장하고 불러오는 모든 동작에서 사용될 계정이기에 위치를 ‘%’로 지정,      모든 IP종류에 대응 가능하게 설정하였다.
이렇게 수면 상황에서 움직임을 감지하면 촬영되는 사진의 URL을 저장할 DB가 생성하였다.    같은 방식으로 ‘외출 시 인상착의를 확인할 사진의 URL저장 table’도 생성하였고, 해당        table의 이름은 ‘HALL’로 설정하였다.
이제 다음은 원격 table인 lightsai 서버 내의 Table을 생성하는 절차이다.
기본적으로 DB에는 FEDERATE 엔진이 설치되어 있지 않게 때문에

install plugin federated soname ‘ha_federated.so’;

위의 명령어를 입력하여 federated 엔진을 설치한다.

Lightsail 서버도 라즈베리파이와 같은 debian 계열의 Ubuntu를 사용하였고, 이로 인해 DB설치   절차는 모두 동일하였다. 다른 것은 DB 내의 table을 생성할 때,table의 구조를 정의하는        과정이였다.

CREATE TABLE SLEEP(
ID INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
URL VARCHAR(250) NOT NULL,
DATE DATETIME DEFAULT NOW())
CHARSET=’UTF8’ ENGINE=FEDERATED CONNCETION=
‘mysql://user_ID:passwd@IP_address:PORT/DB_name/table_name’;

중요한 부분은 connection 부분인데, 앞서 원본이 될 라즈베리파이의 DB에서 생성한           user_ID와 password를 여기에 사용한다. port는 3306, DB_name은 기본적으로 생성되어있는      mysql이며, table_name은 라즈베리에서 만들어둔 table의 이름들이다.
이렇게 local, target DB들을 모두 생성하여 DB관련 절차들은 모두 끝나게 된다.

 1) 카메라를 통한 동작 인식 부분

오픈 소스인 motion 프로그램을 사용하여 동작을 감지하도록 하였는데, event가 발생하면       사진을 찍고 사진 파일의 파일명을 아래에 기재할 ‘storage url – DB 연계 코드’에 인수로      전달하는 동작을 하게끔 설정하였다.


                               -motion 설치-

라즈베리파이에 motion을 설치할 경우, 프로그램 의존성이 맞지 않아 ‘망가진                  고정패키지’라는 에러 메시지가 출력될 수 있는데 이 경우엔 화면에 표기된 ‘의존성이 맞지    않는 패키지’를 직접 설치해주어야 했다. 

sudo apt-get install {해당 패키지명}{=화면에 표기된 호환성 버전}

위 코드를 직접 입력해 호환성 체크까지 모두 끝나면 motion이 설치되는데, 중요한 것은       인식 민감도인 ‘threshold’ 부분과 event가 발생시 실행할 script 지정 부분이었다. motion의      설정 파일 motion.conf는 /etc/motion 디렉토리에 위치한다.


                             -motion.conf파일-
이 파일에서 수정할 곳은 크게  ‘사진, 비디오 파일 저장 위치’ 와 ‘threshold’, ‘event script’다.

############################################################
# System control configuration parameters
############################################################

# Start in daemon (background) mode and release terminal.
daemon off

# Start in Setup-Mode, daemon disabled.
setup_mode off

# File to store the process ID.
; pid_file value

# File to write logs messages into.  If not defined stderr and syslog is used.
; log_file value

# Level of log messages [1..9] (EMG, ALR, CRT, ERR, WRN, NTC, INF, DBG, ALL).
log_level 6

# Target directory for pictures, snapshots and movies
target_dir /home/pi1/motion_detection


motion.conf의 미디어파일 지정 부분으로 맨 아래의 target_dir 부분에 저장할 위치를 절대       주소 형식으로 기입한다.

############################################################
# Motion detection configuration parameters
############################################################

# Always save pictures and movies even if there was no motion.
emulate_motion off

# Threshold for number of changed pixels that triggers motion.
threshold 2000

# Noise threshold for the motion detection.
; noise_level 32

# Despeckle the image using (E/e)rode or (D/d)ilate or (l)abel.
despeckle_filter EedDl

# Number of images that must contain motion to trigger an event.
minimum_motion_frames 1

# Gap in seconds of no motion detected that triggers the end of an event.
event_gap 10

동작 인식의 민감도와 event 사이의 시간 간격을 지정하는 부분이다. 기본적으로 motion은      연속된 사진을 찍어 사진의 픽셀 변화를 계산하고 이를 기반으로 동작의 크기를 인식하는     방식이기에 threshold는 pixel의 변화 허용도를 의미하는 것과 같았습니다. 기본적으론 1500의    수치로 설정되어 있으나 우리가 필요한 수준보다 더 민감한 반응을 보여 2000으로 늘리게     되었다. 
event 간의 간격은 기본 설정의 60초(1분)이 너무 길어 10초로 재설정하였다.

############################################################
# Script execution configuration parameters
############################################################

# Command to be executed when an event starts.
; on_event_start value

on_picture_save python3  /home/pi1/motion.py %f

# Command to be executed when an event ends.
; on_event_end value


event가 시작, 발생, 종료 될 때 각각 어떤 script를 실행할지 지정하는 부분이다. 
우리는 event가 시작될 때 사진을 촬영하고 save한 뒤, 촬영한 사진의 파일명을 motion.py       파일에 전달하게끔 설정하였다. %f를 통해 ‘절대경로가 포함된 파일명’을 전달하게끔          하였다.


############################################################
# Picture output configuration parameters
############################################################

# Output pictures when motion is detected
picture_output best

# File name(without extension) for pictures relative to target directory
picture_filename="%Y%m%d%H%M"

이 부분은 사진이 event의 어떤 시점에 촬영될지 지정하고 저장 시의 파일 명 서식을          지정하는 부분이다. file_name은 기본 설정대로 시간이 표기되게끔 수정하지 않았고,           picture_output은 best로 지정하여 event의 한가운데 시점에 촬영되게끔 하였다.


############################################################
# Movie output configuration parameters
############################################################

# Create movies of motion events.
movie_output off

# Maximum length of movie in seconds.
movie_max_time 60

마지막으로 동영상 파일 관련 부분이다. 스트리밍도 가능하였으나 수면상황은 사생활 침해의    우려가 크고, 무엇보다 보호 대상자들이 ‘감시’당하는 것과 같은 상황에 놓여있게 만들        우려가 있어 사진만 저장, 전달하는 방향으로 계획하였습니다. 그렇기에 동영상 파일은        저장되지 않게끔 movie_output을 off로 설정하였다.










2) Script python 파일인 motion.py
우선 firebase 기능을 사용 가능하게 해줄 패키지를 라즈베리파이에 설치해주었다.

import pymysql
import subprocess
import os
import time
from datetime import datetime
from time import sleep
import sys
import requests
import firebase_admin
from firebase_admin import credentials
from firebase_admin import storage
from uuid import uuid4

file_name=sys.argv[1] #motion에서 event 발생시 사진만 찍고 저장함. 이 때, %f로 절대 경    로+파일 이름 string을 인수로 받아 file_name에 저장함.
print("{}".format(file_name))
PROJECT_ID="health-2ab9e" #firebase storage에서 프로젝트 이름
cred = credentials.Certificate("/home/pi1/health.json") #firebase storage_public_key location 입력    란(절대경로)
default_app 
= firebase_admin.initialize_app(cred,{'storageBucket':f"{PROJECT_ID}.appspot.com"})

bucket=storage.bucket() #기본 bucket으로 받아오기. 
                        #다만 보안그룹 설정으로 authorize 조건을 설정한다면 사용자들    이 '읽기만 가능한' 버킷을 따로 구현, 저장할 수도 있을 것.

def fileUpload(file): #firebase storage에 public_key를 이용, 버킷에 접근하여  'file name'을     인수로 받아 해당 이름의 파일을 바로 업로드하는 함수
blob = bucket.blob('captureImages/'+file) #BLOB파일 형식으로 버킷에 저장하되, 임시로 버    킷 내의 'captureImages' 폴더로 저장



    #new token and metadata 설정
new_token = uuid4()
metadata = {"firebaseStorageDownloadTokens": new_token} #access token을 검사
blob.metadata = metadata #업로드 대상 파일의 메타 데이터를 함께 저장

    #uploading the files
blob.upload_from_filename(filename=file_name, content_type='image/jpeg') #만약 라즈베리파이    내의 사진 파일을 저장하려 한다면 '파일 절대 경로'+'파일 이름' 이 file_name 대신 들어    간다.
    #현재는 motion 프로그램 자체에서 이미지 저장과 동시에 "절대경로와 파일 이름"을    전부 %f를 통해 전달받기에 단순 대입으로 끝
print(blob.public_url) #즉각적인 확인을 위해 터미널에 바로 스토리지에 저장된 해당 사진    파일의 url을 출력함. (삭제해도 무방)
    
    #pymysql로 db에 접근하여 url저장을 위한 단계
 conn = pymysql.connect(host = 'localhost', user='user_ID',password='passwd', db='mysql',charset='utf8') #pymysql로 (호스트, 사용자계졍, 비밀번호, 저장할 db명)을    전달해 대상 db에 접근함.
cursor=conn.cursor() #cursor로 db중에서 어떤 table, 어떤 column의 데이터를 수정할 것인가    를 가리킴
sql="INSERT INTO SLEEP(url) VALUES(%s)" #INSERT INTO 명령문으로 TABLE에 새로    운 데이터 column을 삽입하겠다는 쿼리를 미리 선언해둠

url=blob.public_url #firebase storage에 업로드 함과 동시에 url을 받은 외부인이 해당 스토    리지 파일만 열람할 수 있게끔 파일의 url을 요청하는 단계.
cursor.execute(sql,url) #cursor로 sql 쿼리를 전달, url column에 접근하여 url을 집어넣으라는    명령을 수행하는 단계 
conn.commit() 
conn.close() #cursor를 닫아 db 수정을 마침
#------------------------------------------------------------------------ 여기까지가 이미지 파일의 절대 경로를 전달받아 스토리지 서버에 저장함과 동시에 url을 요청, db에 저장하는 함수------------------------------------------------------------#

fileUpload(file_name) #이제 motion에서 파일 저장함과 동시에 image_save_event_script 실행    이 이루어지면 전달받은 %f를 함수 인자로 주어 위의 함수를 시행함.


위 파일들을 시행해본 결과,

        -url이 저장된 DB와 lightsail서버(ubuntu)의 DB가 link된 모습-

실제로 firebase에 저장 후, 반환 받은 url이 라즈베리파이 내의 table에 저장되었고, 이 table의 data가 우분투 기반의 EC2 서버 내에 그대로 뿌려진 모습을 볼 수 있었다.

 3) url 게시용 웹페이지
url을 저장하는 과정은 완료하여 이 url들을 웹 페이지에 출력하는 단계로 넘어가게 되었다.
처음에는 python 기반의 framework 중에서 가볍게 사용할 수 있는 Flask를 기반으로 웹         페이지를 개설하려 하였으나, Flask와 호환이 되는 템플릿 엔진인 jinja2에 대해선 접해볼       기회가 많이 없었고, 국내 데이터 역시 얼마 없었기에 다루기 어렵다고 판단, apache2 와       php로 웹페이지 개발 방향을 바꾸도록 하였다.
앞서 DB간 연계나 url전달 방향을 테스트해보는 과정이 오래 걸렸기에 시간이 매우           촉박했고, 이로 인해 단순히 DB내의 url data를 웹페이지에 출력만 하는 단순하지만           핵심적인 기능만을 구현해보고자 하였다.
해당 웹페이지는 client가 직접적으로 접근이 가능한 EC2 서버에 구축되어야 하는데, 이를      위해 EC2에 apache2와 php를 설치하였다.
각각 sudo apt-get install 명령어를 이용해 설치가 완료되면 웹페이지 프로토콜(HTTP)로 EC2    서버에 접근이 가능하게끔 보안 그룹을 지정 해주어야 하는데, 아래와 같이 AWS의           보안그룹을 설정하여 접근을 허용하도록 하였다.

                       -AWS lightsail 서버의 보안그룹-

HTTP 프로토콜을 통한 접근까지 허용한 뒤, EC2 내의 DB 속 url들을 전달받아 웹페이지에   출력해줄 php파일을 생성하였다.

<!DOCTYPE html>
<html>
<body>
<h2></h2>
<?php
   $conn = mysqli_connect("127.0.0.1", "user_ID", "passwd" , "DB이름");
   $sql = "SELECT URL, DATE FROM table이름";
   $result = mysqli_query($conn, $sql);
   if (mysqli_num_rows($result) > 0) {
   while($row = mysqli_fetch_assoc($result)) {
   echo "URL: " . $row["URL"]. " DATE:" . $row["DATE"]. "<br>";
   }
   }else{
   echo "There are no datas";
   }
   mysqli_close($conn); //DB close
?>
</body>
</html>

아래와 같이 php파일을 작성 후, apache2가 템플릿을 읽어 들이는 root directory인 /var/www     에 저장하였고, http://EC2서버_public IP/php파일명.php 를 통해 웹페이지에 접속하면 아래와    같이 URL과 해당 사진이 찍힌 시간이 나열되는 것을 볼 수 있었다.


                               -웹페이지에 출력된 url-


firebase storage 서버에도 해당 파일명의 사진이 동일 시간대에 저장되어 있는 것을 볼 수     있다.            .
			-firebase storage에도 저장되어 있는 사진-
 4) 카카오톡 구현 부분
Javascript, node.js를 배우고 실제로 적용하는 것에 시간상 한계점이 존재하였고, 이를          보완하고자 버튼을 통한 문답식 chatbot을 구현해보고자 하였다.


				    -프로젝트 chatbot-

		-외출 복장과 수면상황 확인용 웹페이지 url 연결 블록 설정-

처음에 기획한 내용 중 하나는 센서 값에 따라 사용자에게 선제 알람 메시지를 전송하는      것이 있었는데, 해당 기능은 node.js를 새로 공부하면서 해당 api를 개발할 시간이 부족하여    구현을 하는 것에 실패하였다.
다만 이는 조금 더 자유로운 개발 언어 환경을 제공하는 Discord나 telegram등의 메신저들을    이용했다면 수월한 개발이 가능했을 것으로 예상된다.

 
5) 센서 구현 부분

센서를 구현할 때 우리는 영역을 크게 세 개로 나누었다. 첫 번째는 화장실 영역이다.         이곳에서 우리는 MDR_MICRO_A(이하 mdr)라는 레이더 시스템과 HM_10이라는 블루투스      모델을 통하여 연결을 하였다. 아래는 mdr의 아두이노 코드이다.                        
#include <SoftwareSerial.h>
#define RX 8
#define TX 9
 
SoftwareSerial Arduino_to_Radar_Serial(RX, TX);  
int Radar_Signal_Read_Pin = 7; 
int val = 0;

void setup()
{
  pinMode(Radar_Signal_Read_Pin, INPUT); // 디지털 7번핀을 GPIO INPUT으로 설정한다
  pinMode(LED_BUILTIN, OUTPUT); // LED_BUILTIN는 아두이노 보드에 자체적으로 달린 LED이며, 이를 Signal Out핀으로 설정한다
허
  Serial.begin(9600); // Serial 객체는 PC와 Arduino와의 시리얼 통신을 담당하며, Baud Rate = 9600 설정한다
  Arduino_to_Radar_Serial.begin(9600); // Arduino_to_Radar_Serial 객체는 Arduino와 Radar 모듈과의 시리얼 통신을 담당하며, Baud Rate = 9600 설정한다
}
 
void loop()
{
  val = digitalRead(Radar_Signal_Read_Pin);   // Radar로부터의 움직임 신호를 읽어 val 변수에 저장한다.
  digitalWrite(LED_BUILTIN, val);  // val 변수의 값에 따른 LED의 High, Low 상태 결정한다
 
 
  if(val > 0)
  {    
    //값이 측정되었을 경우에 이곳에 할 행동을 추가
  }






  // 시리얼 모니터 -> 아두이노 -> Radar 모듈
  if(Serial.available())
  {
    char Transmit_Char = Serial.read(); // 시리얼 모니터를 통해 전송할 데이터를 1바이트씩 읽고 Transmit_Char 변수에 저장한다
    Arduino_to_Radar_Serial.write(Transmit_Char); // Transmit_Char 변수에 저장된 1바이트 값을 Radar 모듈로 송신한다
    Serial.print(Transmit_Char); // 아두이노 사용자가 자신이 전송한 데이터를 알 수 있도록 Transmit_Char 변수에 저장된 1바이트 값을 시리얼 모니터에 표시한다
  }
  // Radar 모듈 -> 아두이노 -> 시리얼 모니터
  if(Arduino_to_Radar_Serial.available())
  {
    char Receive_Char = Arduino_to_Radar_Serial.read(); // Radar 모듈이 보낸 데이터를 1바이트씩 읽고 Receive_Char 변수에 저장한다
    Serial.print(Receive_Char); // Radar 모듈이 보낸 데이터를 아두이노 사용자가 알 수 있도록 Receive를 해준다
  }
}

위와 같이 mdr코드를 넣고 실행을 하였으며, 문제없이 진행이 되었다. 하지만 실제로 회로 결선을 위하여 mdr센서에 납땜을 하였으나, 레이더 센서 자체가 온도 변화에 매우 민감한 소자였기에 납땜과정에서의 실수로 많은 열이 센서에 가해지게 되어 센서가 제대로 측정을 하지 못하는 문제가 발생하였다.

따라서 이를 수정하기 위하여 우리는 pir 센서를 통하여 인체감지를 대체하기로 하였고, 다음과 같이 코드를 생성하였다.

#include <SoftwareSerial.h>
SoftwareSerial bluetooth(7, 8); // (RX, TX)    // 시리얼 통신 핀 설정 합니다.
const int led_pin = 13;        
const int pir_pin = 3;        
int state = 0;      // 센서 상태 값 저장 변수(0: LOW, 1: HIGH)
int pre_state = 0;
int count = 0;
void setup(void){
 
  Serial.begin(9600);
  Serial.println("");
  bluetooth.begin(9600);
  pinMode(led_pin, OUTPUT);
  pinMode(pir_pin, INPUT);
  delay(10);


  Serial.println();
}
void loop(){
  state = digitalRead(pir_pin);
  digitalWrite(led_pin, LOW);

  if (pre_state==0 && state == 1)
  {
    count ++;
    bluetooth.print("Human Detect!   count : ");
    bluetooth.println(count);    
    digitalWrite(led_pin, HIGH);
  }
  else if(pre_state == 0 && state == 0)
  {
    digitalWrite(led_pin, LOW);
  }
  pre_state = state;
}


이렇게 했을 때 사람이 감지 되게 되면 Human Detect! count : 라는 메시지와 함께 count된     숫자가 보내지게 되는 것을 확인하였다. 이를 라즈베리파에서 받기 위해서는 파이썬 코드를    다음과 같이 작성하여야 한다.

from bluetooth import *
import pymysql

client_socket=BluetoothSocket(RFCOMM)
client_socket.connect(("98:DA:60:03:F7:28", 1))

while True:
    msg = client_socket.recv(1024)
    print("human detected? {}".format(msg))
    conn=pymysql.connect(host='localhost',user='test_ID',password='123456',db='mysql')
    cursor=conn.cursor()
    sql="INSERT INTO BATH(url) VALUES(%s)"
    cursor.execute(sql,msg)
    conn.commit()
    conn.close()
   
print("Finished")
client_socket.close()

이렇게 하고 난 뒤 블루투스 통신을 하게 되면 human detected?라는 메시지 후에              아두이노에서 블루투스를 통한 결과가 전달이 됨을 볼 수 있었다.


다음은 현관문 영역이다. 앞서 문제점에서 언급했던 대로 아두이노에서 카메라를 연결했을     경우 전송과정에서 호환성의 문제가 발생하였기에 라즈베리파이에 직접 웹캠과 PIR센서를     연결하고 그 결과를 데이터베이스에 전송하는 방식으로 구현하였다.                 
import RPi.GPIO as GPIO
import time
import cv2
import pymysql
import subprocess
import os
from datetime import datetime
from time import sleep
import sys
import requests
import firebase_admin
from firebase_admin import credentials
from firebase_admin import storage
from uuid import uuid4

file_name='/home/pi/motion_detection/'
PROJECT_ID="health-2ab9e" 
cred = credentials.Certificate("/home/pi/health.json") 
default_app = firebase_admin.initialize_app(cred,{'storageBucket':f"{PROJECT_ID}.appspot.com"})
bucket=storage.bucket() 

def fileUpload(file): 
    blob = bucket.blob('captureImages_Door/'+file)   
    new_token = uuid4()
    metadata = {"firebaseStorageDownloadTokens": new_token} 
    blob.metadata = metadata   
    blob.upload_from_filename(filename=file_name+file, content_type='image/jpeg') 
    print(blob.public_url) 
    conn = pymysql.connect(host = 'localhost', user='test_ID',password='123456', 
db='mysql',charset='utf8') 
    cursor=conn.cursor() 


    sql="INSERT INTO HALL(url) VALUES(%s)" 
    url=blob.public_url 
    cursor.execute(sql,url) 
    conn.commit() 
    conn.close()
    
def excute_camera():
    subtitle = "pi"
    fixname = datetime.now().strftime("%Y%m%d_%H%M%S") + '.jpg'
    filename = "_".join([subtitle, fixname])
    
    cap = cv2.VideoCapture(0)
    print ('width: {0}, height: {1}'.format(cap.get(3),cap.get(4)))
    cap.set(3,320)
    cap.set(4,240)
    ret, frame = cap.read()
    frame = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    cv2.imshow('frame', frame)
    cv2.imwrite('/home/pi/motion_detection/'+filename ,frame)
    fileUpload(filename)
    

GPIO.setmode(GPIO.BCM)
LED=20
pirPin=13
GPIO.setup(LED, GPIO.OUT)
GPIO.setup(pirPin, GPIO.IN, GPIO.PUD_UP)

while True:

    if GPIO.input(pirPin) == GPIO.LOW:
        print ("no motion!")
        time.sleep(2)
    else:
        GPIO.output(LED,GPIO.HIGH)
        excute_camera()
        print ("yes motion!")
        time.sleep(5)
        if cv2.waitKey(1) & 0xFF == ord('q'):
            break


GPIO.cleanup()
cap.release()
cv2.destroyAllWindows()


GPIO.cleanup()
cap.release()
cv2.destroyAllWindows()



마지막으로 충격감지 센서를 구현한 침대 영역이다. 여기에서는 충격감지센서를     아두이노를 통하여 값을 받고 그 결과 값을 분석하여 정해진 충격량 이상의 값이             측정되었을 경우에 블루투스 통신을 통하여 라즈베리파이에 보내는 형식을 취하였다. 아래는    아두이노에 들어간 소스코드이다.


#include <ADXL345.h>
#include <SoftwareSerial.h>

SoftwareSerial BTSerial(2, 3); // (RX, TX) 통신핀 설정
ADXL345 adxl;
void setup() {
  Serial.begin(9600);// 시리얼 통신 속도 설정 및 시작
  BTSerial.begin(9600);// 블루투스 통신 데이터 속도 설정
  delay(200);
  adxl.powerOn();
  //set activity/ inactivity thresholds (0-255)
  adxl.setActivityThreshold(75); //62.5mg per increment
  adxl.setInactivityThreshold(75); //62.5mg per increment
  adxl.setTimeInactivity(10); // how many seconds of no activity is inactive?
  //look of activity movement on this axes - 1 == on; 0 == off 
  adxl.setActivityX(1);
  adxl.setActivityY(1);
  adxl.setActivityZ(1);
  //look of inactivity movement on this axes - 1 == on; 0 == off
  adxl.setInactivityX(1);
  adxl.setInactivityY(1);
  adxl.setInactivityZ(1);
  //setting all interupts to take place on int pin 1
  adxl.setInterruptMapping( ADXL345_INT_ACTIVITY_BIT,     ADXL345_INT1_PIN );
  adxl.setInterruptMapping( ADXL345_INT_INACTIVITY_BIT,   ADXL345_INT1_PIN );
  //register interupt actions - 1 == on; 0 == off
  adxl.setInterrupt( ADXL345_INT_ACTIVITY_BIT,   1);
  adxl.setInterrupt( ADXL345_INT_INACTIVITY_BIT, 1);
  delay(50);
}



void loop() {
  int x,y,z;
  adxl.readAccel(&x, &y, &z); 
   byte interrupts = adxl.getInterruptSource();
  //inactivity
  if(adxl.triggered(interrupts, ADXL345_INACTIVITY)){
    delay(5000);
  }
  //activity
  if(adxl.triggered(interrupts, ADXL345_ACTIVITY)){
    BTSerial.println("Y");
    delay(5000);
  }
  delay(1000);
}


또한 이 결과를 블루투스 통신을 통하여 라즈베리파이에서 받아들여야하기에 아래와 같은     파이썬 코드 또한 작성을 해주었다.

import subprocess
import os
import time
from datetime import datetime
from time import sleep
import sys
from bluetooth import *
import pymysql

client_socket=BluetoothSocket(RFCOMM)
client_socket.connect(("98:DA:60:07:07:65", 1))

while True:
    msg = client_socket.recv(1024)
    print('fall!')
    conn=pymysql.connect(host='localhost',user='user_ID',password='passwd',db='mysql')
    cursor=conn.cursor()
    sql="INSERT INTO FALL(url) VALUES(%s)"
    cursor.execute(sql,msg)
    conn.commit()
    conn.close()
client_socket.close()

5. 결론 및 기대효과

최근 고령화 시대가 진행됨에 따라 기대수명이 높아지고 그로 인해 고령 인구와 독거노인 가구 비율이 높아지고 있다. 이에 독거노인은 사회적으로 고립되어 여러 어려움에 직면해 있는 상태이다. 현재 한국에서는 독거노인들의 사회적 보장제도에 미흡한 면이 존재하고 있고 이 때문에 독거노인 지원 시스템의 필요성이 높아졌다. 우리는 이를 위해 라즈베리파이와 아두이노를 활용한 센서 기반의 독거노인 모니터링 시스템을 구축하였다. 이 시스템은 PIR 센서, 기울기 센서, 카메라를 기반으로 각각 현관문, 화장실, 낙상 사건에 대한 각각의 상황을 파악하고 그를 바탕으로 독거노인의 상태를 확인할 수 있게 시스템을 구현하고 위험시 대처를 가능하게 만들었다. 이를 통해 거동이 불편하거나 질병을 앓고 있어 지속 관찰이 필요한 독거노인의 안전과 건강관리를 유의미하게 확인할 수 있으며 실시간으로 사진에 찍힌 독거노인의 상황을 모니터링해서 대처할 수 있다. 독거노인의 문제는 단지 사고에만 국한하는 것이 아닌 사회적인 관심이 부족한 점 또한 많다. 이러한 점은 독거노인들의 감정적 문제로도 이어지는데 사회적으로 고립되어 있다는 점이 그들에게는 매우 큰 불안감으로 작용할 수 있다. 이러한 관점에서 우리의 시스템은 원격으로 독거노인의 상황 파악이 가능하고 위험에 대한 대처가 가능해 독거노인들께 심리적 안정감과 고독사를 방지하는 효과도 기대할 수 있다. 치매 노인의 경우 실종률이 매우 높은데 우리는 치매 노인의 출입 기록과 출입 시 복장에 대한 사진을 실시간으로 촬영함에 따라 실종 시 인상착의를 쉽게 파악해 사회적으로 문제가 된 치매 노인의 실종률을 낮출 수 있을 것으로 기대가 된다. 마지막으로 실시간으로 사고에 대한 인식이 가능하여 신속하게 사고에 대한 후속 조치가 가능하여 2차 사고의 예방 효과 또한 기대할 수 있다. 이러한 여러 가지의 기대효과로 현재 실시간으로 중대한 문제인 독거노인의 고독사를 방지하고 그들에게 쉽고 저렴한 방법으로 도움을 줄 수 있다.


7. 후기
전체적인 프로그램의 구성에 방향을 정하지 못하고 있을 때 최한고 교수님께 조언을 구해 전체적인 시스템 방향을 정하고 구성을 짜임새 있게 구성할 수 있었다. 설계 방향을 정하고 ‘한 권으로 끝내는 아두이노 입문’. ‘IOT 사물인터넷을 위한 라즈베리파이4’ 도서, 그리고 유튜브 강의를 참고했다. 센서는 충격 감지 센서, pir 센서, 웹캠을 사용했다. 전체적인 흐름으로는, 아두이노에 연결된 센서 데이터를 라즈베리파이로 보낼 때 블루투스 모듈을 사용하고 이때 라즈베리파이와 연결된 웹캠이 사진을 촬영한다. 이 데이터는 구글의 클라우드 서비스인 firebase에 저장하고 이때 사진들은 각각 고유의 URL을 갖게 된다. 즉시 URL들은 공개형 Database인 MYSQL에 저장되고, 동시에 AWS의 Lightsail 서버에서 MYSQL을 통해 url 데이터를 받아온다. 이후 html을 사용해 개설한 웹사이트에 URL들이 올라간다. 그리고 이 URL은 카카오톡 챗봇을 통해 쉽게 접근할 수 있다. 라즈베리파이와 Lightsail 서버의 OS로는 우분투 환경을 사용했고 언어는 python을 사용했다. 이번 설계를 통해 코딩과 ip 주소, 경로설정으로 하드웨어와 소프트웨어들의 유기적인 연결을 이루어내면서 IoT 분야에 대해 자신감과 흥미를 얻게 되었다.


팀원간 역할 분담
성명
역할
참여도(%)
김형진
raspberrypi 및 arduino
33
지원섭
mysql 및 firebase
33
최윤호
AWS, html 및 chatbot
33



비용 분석
항목
세부항목
소요비용
재료비
라즈베리파이 2개
325,000
라즈베리파이용 어댑터 2개
12,800
라즈베리파이용 케이스
6,000
라즈베리파이용 8MP 카메라 2개
69,700
라즈베리파이용 SD카드 32기가 2개
12,300
라즈베리파이 7인치 터치스크린
91,300
브레드 보드
1,710
PIR센서 HC-SR501
6,600
진동감지센서 SW-420
1,300
아두이노 우노 R3 CH340
10,000
가속도 센서 ADXL345
2,420
블루투스 모듈 HC-06
13,560
HDMI TO MICRO HDMI 케이블
2,540
USB 카드 리더기 CR015
1,600
와이파이 모듈 N150mini
6,900
라즈베리파이 배송비
7,900
브레드 보드 배송비
2,750
PIR센서 배송비
6,000
진동감지 센서 배송비
2,500
아두이노 우노 배송비
3,000
가속도 센서 배송비
2,700
블루투스 모듈 배송비
6,000
HDMI 케이블 배송비
3,000
와이파이 모듈 배송비
2,500
시제품가공비
ㆍ
0
다과비
회의비
99,600
합계

699,680


참고문헌

(1) 서민우 박준원 (2021) 한권으로 끝내는 아두이노 입문 + 실전(종합편), 앤써북
(2) 최주호 김재범 정동진 (2019) IoT 사물인터넷을 위한 라즈베리파이 4 정석, 앤써북



별첨 

-작품사진


-------------------------------------------------------------
