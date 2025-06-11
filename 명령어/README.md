# 리눅스 명령어 50개 완전 정리

## 목차
1. [파일 및 디렉터리 조작](#파일-및-디렉터리-조작)
2. [파일 내용 확인](#파일-내용-확인)
3. [파일 검색 및 필터링](#파일-검색-및-필터링)
4. [파일 압축 및 아카이브](#파일-압축-및-아카이브)
5. [시스템 정보](#시스템-정보)
6. [프로세스 관리](#프로세스-관리)
7. [네트워크](#네트워크)
8. [권한 및 소유권](#권한-및-소유권)
9. [텍스트 처리](#텍스트-처리)
10. [기타 유용한 명령어](#기타-유용한-명령어)

---

## 파일 및 디렉터리 조작

### 1. ls - 파일 및 디렉터리 목록 표시
```bash
# 기본 사용법
ls

# 옵션과 함께 사용
ls -la          # 숨김파일 포함, 자세한 정보
ls -lh          # 파일 크기를 읽기 쉽게 표시
ls -lt          # 시간순 정렬
```

### 2. cd - 디렉터리 변경
```bash
cd /home/user   # 절대 경로로 이동
cd ..           # 상위 디렉터리로 이동
cd ~            # 홈 디렉터리로 이동
cd -            # 이전 디렉터리로 이동
```

### 3. pwd - 현재 작업 디렉터리 출력
```bash
pwd             # 현재 디렉터리의 전체 경로 표시
```

### 4. mkdir - 디렉터리 생성
```bash
mkdir mydir     # 단일 디렉터리 생성
mkdir -p dir1/dir2/dir3  # 중간 디렉터리까지 모두 생성
mkdir dir1 dir2 dir3     # 여러 디렉터리 동시 생성
```

### 5. rmdir - 빈 디렉터리 삭제
```bash
rmdir mydir     # 빈 디렉터리 삭제
rmdir -p dir1/dir2/dir3  # 중간 디렉터리까지 모두 삭제
```

### 6. rm - 파일 및 디렉터리 삭제
```bash
rm file.txt     # 파일 삭제
rm -r mydir     # 디렉터리와 내용 모두 삭제
rm -f file.txt  # 강제 삭제 (확인 없이)
rm -rf mydir    # 디렉터리 강제 삭제
```

### 7. cp - 파일 및 디렉터리 복사
```bash
cp file1.txt file2.txt          # 파일 복사
cp -r dir1 dir2                 # 디렉터리 복사
cp -i file1.txt file2.txt       # 덮어쓰기 확인
cp file1.txt file2.txt /tmp/    # 여러 파일을 디렉터리에 복사
```

### 8. mv - 파일 및 디렉터리 이동/이름변경
```bash
mv file1.txt file2.txt  # 파일 이름 변경
mv file.txt /tmp/       # 파일 이동
mv dir1 dir2           # 디렉터리 이름 변경
```

### 9. ln - 링크 생성
```bash
ln file.txt hardlink.txt        # 하드링크 생성
ln -s /path/to/file symlink.txt # 심볼릭링크 생성
```

### 10. find - 파일 및 디렉터리 검색
```bash
find /path -name "*.txt"        # 특정 패턴의 파일 검색
find /path -type f -size +1M    # 1MB 이상의 파일 검색
find /path -mtime -7            # 7일 이내 수정된 파일
find /path -name "*.log" -delete # 검색 후 삭제
```

---

## 파일 내용 확인

### 11. cat - 파일 내용 출력
```bash
cat file.txt                    # 파일 전체 내용 출력
cat file1.txt file2.txt         # 여러 파일 연결해서 출력
cat -n file.txt                 # 줄 번호와 함께 출력
```

### 12. less - 파일 내용을 페이지 단위로 출력
```bash
less file.txt                   # 페이지 단위로 파일 내용 보기
# 사용법: Space(다음페이지), b(이전페이지), q(종료)
```

### 13. more - 파일 내용을 페이지 단위로 출력
```bash
more file.txt                   # 페이지 단위로 파일 내용 보기
```

### 14. head - 파일의 처음 부분 출력
```bash
head file.txt                   # 처음 10줄 출력
head -n 20 file.txt             # 처음 20줄 출력
head -c 100 file.txt            # 처음 100바이트 출력
```

### 15. tail - 파일의 마지막 부분 출력
```bash
tail file.txt                   # 마지막 10줄 출력
tail -n 20 file.txt             # 마지막 20줄 출력
tail -f /var/log/syslog         # 실시간으로 파일 끝 부분 모니터링
```

---

## 파일 검색 및 필터링

### 16. grep - 텍스트 패턴 검색
```bash
grep "pattern" file.txt         # 파일에서 패턴 검색
grep -r "pattern" /path/        # 디렉터리에서 재귀적 검색
grep -i "pattern" file.txt      # 대소문자 구분 안함
grep -n "pattern" file.txt      # 줄 번호와 함께 출력
grep -v "pattern" file.txt      # 패턴이 없는 줄 출력
```

### 17. awk - 텍스트 처리 도구
```bash
awk '{print $1}' file.txt       # 첫 번째 필드 출력
awk -F: '{print $1}' /etc/passwd # 구분자를 :으로 설정
awk '/pattern/ {print}' file.txt # 패턴이 있는 줄 출력
```

### 18. sed - 스트림 에디터
```bash
sed 's/old/new/g' file.txt      # 문자열 치환
sed -i 's/old/new/g' file.txt   # 파일 직접 수정
sed -n '1,5p' file.txt          # 1-5번째 줄만 출력
sed '/pattern/d' file.txt       # 패턴이 있는 줄 삭제
```

### 19. sort - 텍스트 정렬
```bash
sort file.txt                   # 알파벳순 정렬
sort -n file.txt                # 숫자순 정렬
sort -r file.txt                # 역순 정렬
sort -k2 file.txt               # 두 번째 필드로 정렬
```

### 20. uniq - 중복 행 제거
```bash
uniq file.txt                   # 연속된 중복 행 제거
sort file.txt | uniq            # 모든 중복 행 제거
uniq -c file.txt                # 중복 횟수와 함께 출력
uniq -d file.txt                # 중복된 행만 출력
```

---

## 파일 압축 및 아카이브

### 21. tar - 아카이브 생성 및 추출
```bash
tar -cvf archive.tar files/     # 아카이브 생성
tar -xvf archive.tar            # 아카이브 추출
tar -czvf archive.tar.gz files/ # gzip 압축과 함께 아카이브
tar -xzvf archive.tar.gz        # gzip 압축 해제와 함께 추출
tar -tvf archive.tar            # 아카이브 내용 확인
```

### 22. gzip - 파일 압축
```bash
gzip file.txt                   # 파일 압축 (file.txt.gz 생성)
gzip -d file.txt.gz             # 압축 해제
gzip -c file.txt > compressed.gz # 원본 파일 유지하며 압축
```

### 23. gunzip - gzip 압축 해제
```bash
gunzip file.txt.gz              # 압축 해제
```

### 24. zip - ZIP 아카이브 생성
```bash
zip archive.zip file1 file2     # ZIP 파일 생성
zip -r archive.zip directory/   # 디렉터리를 재귀적으로 압축
```

### 25. unzip - ZIP 아카이브 추출
```bash
unzip archive.zip               # ZIP 파일 추출
unzip -l archive.zip            # ZIP 파일 내용 확인
unzip archive.zip -d /path/     # 특정 디렉터리에 추출
```

---

## 시스템 정보

### 26. ps - 실행 중인 프로세스 표시
```bash
ps                              # 현재 터미널의 프로세스
ps aux                          # 모든 프로세스 상세 정보
ps -ef                          # 모든 프로세스 전체 정보
ps -u username                  # 특정 사용자의 프로세스
```

### 27. top - 실시간 프로세스 모니터링
```bash
top                             # 실시간 프로세스 정보
top -u username                 # 특정 사용자의 프로세스만
# 사용법: q(종료), k(프로세스 종료), M(메모리순 정렬)
```

### 28. htop - 향상된 프로세스 모니터링
```bash
htop                            # top의 향상된 버전
```

### 29. df - 디스크 사용량 확인
```bash
df                              # 파일시스템 사용량
df -h                           # 읽기 쉬운 형태로 표시
df -i                           # inode 사용량 표시
```

### 30. du - 디렉터리 사용량 확인
```bash
du -h directory/                # 디렉터리 사용량 (읽기 쉽게)
du -sh directory/               # 총 사용량만 표시
du -ah directory/               # 모든 파일 크기 표시
```

### 31. free - 메모리 사용량 확인
```bash
free                            # 메모리 사용량
free -h                         # 읽기 쉬운 형태로 표시
free -m                         # MB 단위로 표시
```

### 32. uname - 시스템 정보 확인
```bash
uname -a                        # 모든 시스템 정보
uname -r                        # 커널 버전
uname -m                        # 아키텍처 정보
```

---

## 프로세스 관리

### 33. kill - 프로세스 종료
```bash
kill PID                        # 프로세스 정상 종료
kill -9 PID                     # 프로세스 강제 종료
kill -TERM PID                  # SIGTERM 신호 전송
```

### 34. killall - 프로세스명으로 종료
```bash
killall process_name            # 프로세스명으로 모든 프로세스 종료
killall -9 process_name         # 강제 종료
```

### 35. jobs - 백그라운드 작업 확인
```bash
jobs                            # 현재 백그라운드 작업 목록
jobs -l                         # PID와 함께 표시
```

### 36. bg - 작업을 백그라운드로 전환
```bash
bg %1                           # 1번 작업을 백그라운드로
```

### 37. fg - 백그라운드 작업을 포그라운드로
```bash
fg %1                           # 1번 작업을 포그라운드로
```

### 38. nohup - 로그아웃 후에도 실행 유지
```bash
nohup command &                 # 명령을 백그라운드에서 실행
```

---

## 네트워크

### 39. ping - 네트워크 연결 테스트
```bash
ping google.com                 # 호스트에 ping 전송
ping -c 4 google.com            # 4번만 ping 전송
ping -i 2 google.com            # 2초 간격으로 ping
```

### 40. wget - 파일 다운로드
```bash
wget http://example.com/file.txt # 파일 다운로드
wget -c http://example.com/file.txt # 중단된 다운로드 재개
wget -r http://example.com/     # 재귀적 다운로드
```

### 41. curl - URL에서 데이터 전송/수신
```bash
curl http://example.com         # URL 내용 출력
curl -o file.txt http://example.com/file.txt # 파일로 저장
curl -I http://example.com      # 헤더 정보만 확인
```

### 42. netstat - 네트워크 연결 상태 확인
```bash
netstat -a                      # 모든 연결 표시
netstat -l                      # 리스닝 포트만 표시
netstat -p                      # PID와 프로세스명 표시
```

---

## 권한 및 소유권

### 43. chmod - 파일 권한 변경
```bash
chmod 755 file.txt              # 숫자로 권한 설정
chmod u+x file.txt              # 소유자에게 실행 권한 추가
chmod -R 644 directory/         # 재귀적으로 권한 변경
```

### 44. chown - 파일 소유권 변경
```bash
chown user:group file.txt       # 소유자와 그룹 변경
chown user file.txt             # 소유자만 변경
chown -R user:group directory/  # 재귀적으로 소유권 변경
```

### 45. chgrp - 파일 그룹 변경
```bash
chgrp group file.txt            # 그룹 변경
chgrp -R group directory/       # 재귀적으로 그룹 변경
```

---

## 텍스트 처리

### 46. wc - 단어, 행, 문자 수 계산
```bash
wc file.txt                     # 행, 단어, 문자 수
wc -l file.txt                  # 행 수만 계산
wc -w file.txt                  # 단어 수만 계산
wc -c file.txt                  # 문자 수만 계산
```

### 47. cut - 텍스트 필드 추출
```bash
cut -d: -f1 /etc/passwd         # 콜론으로 구분된 첫 번째 필드
cut -c1-10 file.txt             # 1-10번째 문자 추출
```

---

## 기타 유용한 명령어

### 48. history - 명령어 기록 확인
```bash
history                         # 명령어 기록 전체 표시
history 10                      # 최근 10개 명령어
history | grep "pattern"        # 특정 패턴의 명령어 검색
```

### 49. which - 명령어 위치 찾기
```bash
which ls                        # ls 명령어의 위치
which python                    # python 명령어의 위치
```

### 50. man - 매뉴얼 페이지 확인
```bash
man ls                          # ls 명령어 매뉴얼
man -k keyword                  # 키워드로 매뉴얼 검색
```

