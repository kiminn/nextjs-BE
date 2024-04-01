## 백엔드 서버 세팅하기
    ### node.js 
        1. LTS 설치
        2. DB → 포스트 그래 SQL 사용
            - 포스트그래스랑 비밀번호는 세팅할 때 사용됨. (무조건 기억해두기)
        3. Redis → 로그인 시 사용됨
            - 하지만 윈도우에서는 Redis 설치가 불가능함! 그 대체품으로 Memurai라는 레디스 대체품을 설치.(memurai는 redis와 호환가능함!)
            - pg admin
            - npx prisma migrate dev 명령어 입력 필수
            - schema public 밑으로 테이블 생성 → 실제 데이터 확인 가능
            - 유저를 보고싶다 → 뷰 데이터

## 로그인과 회원가입 실제로 하기
    ### 서버 액션
        1. 주의할 점→ 서버에서 실패가 떠도 우리에게 바로 보여지지 않음(터미널에서 체크는 가능)
        2. 회원가입 진행 시 `credentials: ‘include’` 꼭 넣어주기. 그래야지 쿠키 전달이 가능하다!
        3. session을 사용할 시 쿠키가 브라우저에 등록이 되어야 하는데, 그걸 위해서 `credentials: ‘include’` 가 필요하기 때문.
    ### rewrite
        1. 업로드 폴더가 프론트 서버 주소로 되어있지만 실제 이미지 업로드는 백엔드에 되어 있음! → 주소 변경 필요
        2. next-config.js 파일 안에 `[localhost/uplode/:slug](http://localhost/uplode/:slug)` 로 변경 → 자동으로 요청을 저기로 보내도록 변경


    ## 업로드 이미지 미리보기
    ###  스크롤바 대신 자동으로 영역 늘리기
        -  `react-textarea-autosize` 사용
    ### 미리보기
        1. dataURL → 이미지 데이터를 문자열로 나타낸 것.(img src에 사용 가능)
        2. array buffer을 뺀 이유 → `readAsDataURL`하면 무조건 string으로 나옴