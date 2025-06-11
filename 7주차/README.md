# 0418

## chap 06
ps
sleep 10
sleep 10 &

![Image](https://github.com/user-attachments/assets/b81a91ab-5d93-4c12-bc80-0be66bf0adb3)

![Image](https://github.com/user-attachments/assets/59f1ea7c-b6cd-435f-9c00-f7f9a3b18cdd)

![Image](https://github.com/user-attachments/assets/a192b6d2-a80b-497a-b990-cfc8542d3e69)

# 프로세스(Process)

## 프로세스란?

실행중인 프로그램을 **프로세스(process)**라고 한다.

## 프로세스 번호

각 프로세스는 유일한 프로세스 번호 **PID**를 갖는다.

## 부모 프로세스

각 프로세스는 부모 프로세스에 의해 생성된다.

## 프로세스의 종류

### 시스템 프로세스
- 시스템 운영에 필요한 기능을 수행하는 프로세스
- 어떤 서비스를 위해 부팅시 생성되는 데몬 프로세스가 대표적인 예

### 사용자 프로세스
- 사용자의 명령 혹은 프로그램을 실행시키기 위해 생성된 프로세스

## 프로세스 상태 보기: ps (process status)

### 사용법
```bash
$ ps [-옵션]
```
현재 시스템 내에 존재하는 프로세스들의 실행 상태를 요약해서 출력한다.

### 기본 사용 예시
```bash
$ ps
  PID TTY          TIME CMD
 1519 pts/3    00:00:00 bash
 1551 pts/3    00:00:00 ps
```

### ps -f 옵션 (상세 정보)
```bash
$ ps -f
UID        PID  PPID  C STIME TTY          TIME CMD
chang     1519  1518  0 17:40 pts/3    00:00:00 /bin/bash
chang     1551  1519  0 17:40 pts/3    00:00:00 ps -f
```

### ps -ef 옵션 (모든 프로세스)
```bash
$ ps -ef | more
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0  9월30 ?        00:00:23 /sbin/init auto noprompt
root         2     0  0  9월30 ?        00:00:00 [kthreadd]
root         3     2  0  9월30 ?        00:00:00 [rcu_gp]
root         4     2  0  9월30 ?        00:00:00 [rcu_par_gp]
root         6     2  0  9월30 ?        00:00:00 [kworker/0:0H-events_highpri]
root         9     2  0  9월30 ?        00:00:00 [mm_percpu_wq]
root        10     2  0  9월30 ?        00:00:00 [rcu_tasks_rude_]
root        11     2  0  9월30 ?        00:00:00 [rcu_tasks_trace]
root        12     2  0  9월30 ?        00:00:03 [ksoftirqd/0]
root        13     2  0  9월30 ?        00:01:07 [rcu_sched]
root        14     2  0  9월30 ?        00:00:02 [migration/0]
root        24     2  0  9월30 ?        00:00:00 [netns]
root        25     2  0  9월30 ?        00:00:00 [inet_frag_wq]
root        26     2  0  9월30 ?        00:00:00 [kauditd]
...
--More--
```

## ps 명령어 필드 설명

- **UID**: 프로세스 소유자의 사용자 ID
- **PID**: 프로세스 ID (고유 번호)
- **PPID**: 부모 프로세스 ID
- **C**: CPU 사용률
- **STIME**: 프로세스 시작 시간
- **TTY**: 터미널 정보
- **TIME**: CPU 사용 시간
- **CMD**: 실행된 명령어
