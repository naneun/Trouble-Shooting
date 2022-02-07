- # Bulk Insert
  - Bulk Insert 란?
    - 한 번에 여러 튜플을 입력하는 방법  <br><br>
    ```
    Normal Insert
    
    INSERT TABLE VALUES()
    INSERT TABLE VALUES()
    INSERT TABLE VALUES()
    ...
    ```
    ```
    Bulk Insert
    
    INSERT TABLE VALUES(), (), (), ...
    ```    
    
  - ❗ Bulk Insert 시 한 번에 너무 많은 데이터를 삽입하는 경우 오류가 발생할 수 있다.  
    - 전송 가능한 패킷의 크기(16M)가 보다 MySQL 에서 처리할 수 있는 데이터의 크기(1M)가 작기 때문에 발생하는 문제
  <br>
  
  > #### 💭 100만 건의 데이터를 입력한다고 가정해보자  <br>
  > - 한 번에 ***100만*** 건의 데이터를 입력한다면?  <br><br>
  >   ![SmartSelectImage_2022-02-08-07-34-09](https://user-images.githubusercontent.com/47964708/152883827-a5a86fd7-e034-49e6-a392-cce1a50378fb.png)  
  >   ![SmartSelectImage_2022-02-08-07-35-06](https://user-images.githubusercontent.com/47964708/152883836-00fb3e5e-47a4-4519-8bd5-31ed77c2286f.png)  <br>
  > - ***10만*** 건씩 ***10번*** 에 걸쳐 데이터를 입력한다면?  <br><br>
  >   ![SmartSelectImage_2022-02-08-07-34-26](https://user-images.githubusercontent.com/47964708/152883833-5107f4d9-9618-4800-8892-2c609efe8130.png)  
  >   ![SmartSelectImage_2022-02-08-05-36-14](https://user-images.githubusercontent.com/47964708/152867994-6df98818-56ca-40f1-95e8-3a32d86c134a.png)  
  > - 100만 건의 데이터가 10초 내외 (❕ 테이블 구조에 따라 달라질 수 있다) 로 입력이 완료됨을 확인할 수 있다.  <br><br>
  >   ![SmartSelectImage_2022-02-08-05-37-31](https://user-images.githubusercontent.com/47964708/152867988-9f0b401b-1005-4353-9da7-634643334d65.png)  
  ---
  > ➕ MySQL 설정 변수 (max_allowed_packet) 값을 수정하여 전송 가능한 패킷의 크기를 조절할 수 있다.
  >```
  > # vi /etc/mysql/my.cnf
  > ```
  > 
  > ```
  > [mysqld]
  > max_allowed_packet = 32M
  > ```
