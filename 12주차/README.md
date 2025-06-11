# 0523

## chap9


# 👨‍👦 부모 프로세스와 자식 프로세스 구분

## 📌 fork() 함수
- 새로운 프로세스를 생성하는 시스템 호출
- 호출 시 **부모 프로세스는 자식 프로세스의 PID를 리턴**  
  **자식 프로세스는 0을 리턴**

---

## 📌 부모/자식 프로세스 구분 방법

```c
pid_t pid;
pid = fork();

if (pid == 0) {
    // 자식 프로세스 실행 코드
} else {
    // 부모 프로세스 실행 코드
}

```

![image](https://github.com/user-attachments/assets/2b9f0cf2-cbcd-4ba5-ad19-93a26fac2d38)

## fork1.c

![image](https://github.com/user-attachments/assets/689935f0-ce6e-4b03-80cf-8be9dcb2c846)
![image](https://github.com/user-attachments/assets/4f058bed-3ade-4eb8-b1bd-90295faa794b)


## fork2.c
![image](https://github.com/user-attachments/assets/f2806a96-118b-484b-bdf0-4aaea84ed61a)
![image](https://github.com/user-attachments/assets/9bbed3c2-f559-4252-90e3-be58c3713b7a)

## fork3.c
![image](https://github.com/user-attachments/assets/a305a68e-2c93-482e-9912-ba25733d5a19)
![image](https://github.com/user-attachments/assets/efa0893b-cc93-4999-9cf3-3f519364ec23)

## wait() 프로세스 기다리기
### fork4.c
![image](https://github.com/user-attachments/assets/13fceca2-c81a-4600-864d-99d7645e0f43)
![image](https://github.com/user-attachments/assets/55c13a22-e67a-442c-a607-8b1eea472d33)

### fork5.c
![image](https://github.com/user-attachments/assets/4b30296f-7851-408d-b73e-c02292ef29a8)
![image](https://github.com/user-attachments/assets/919a187b-d454-4d4e-b691-3ae764d9b3f3)




