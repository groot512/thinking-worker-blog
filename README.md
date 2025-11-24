flowchart TD
    %% 노드 스타일 정의
    classDef start fill:#2C3E35,stroke:#E3ECD6,stroke-width:2px,color:#E3ECD6;
    classDef process fill:#F9F9F2,stroke:#8FB983,stroke-width:2px,color:#2C3E35;
    classDef decision fill:#E3ECD6,stroke:#4A7A5E,stroke-width:2px,color:#2C3E35;
    classDef github fill:#fff,stroke:#333,stroke-width:2px,color:#333;
    classDef tistory fill:#ff6c00,stroke:#fff,stroke-width:2px,color:#fff;
    classDef endstate fill:#4A7A5E,stroke:#2C3E35,stroke-width:2px,color:#fff;

    %% 1단계: 기획 및 집필
    Start([🚀 Start: 주제 선정 & 대화]):::start --> Brainstorm[🧠 브레인스토밍 & 초안 작성]:::process
    Brainstorm --> Review[📝 수정 및 보완 <br/>(이미지/주석/인용구 추가)]:::process
    Review --> DraftComplete[✨ 콘텐츠(HTML) 완성]:::process

    %% 2단계: 배포 방식 결정
    DraftComplete --> Decision{📡 배포 채널 선택}:::decision

    %% 3-A: GitHub 루트
    Decision -- GitHub Page --> GitHubRoute[📂 GitHub용 포맷팅]:::github
    GitHubRoute --> ExtCSS[🎨 외부 CSS 분리 <br/> assets/style.css]:::process
    ExtCSS --> CleanHTML[매거진 형태 HTML 생성 <br/> volX.html]:::process
    CleanHTML --> LinkUpdate[🔗 Index 및 이전 화 링크 연결]:::process
    LinkUpdate --> PushGitHub[🚀 Git Push & Deploy]:::endstate

    %% 3-B: Tistory 루트
    Decision -- Tistory Blog --> TistoryRoute[🧡 Tistory용 포맷팅]:::tistory
    TistoryRoute --> IntCSS[🎨 내부 CSS 병합 <br/> style 태그 내장]:::process
    IntCSS --> Override[🛡️ 스킨 방어 코드 적용 <br/> !important / Body Hack]:::process
    Override --> BoxFooter[📦 레이아웃 최적화 <br/> Footer 박스형 / 스크롤바 성형]:::process
    BoxFooter --> CopyPaste[📋 HTML 모드 붙여넣기 & 발행]:::endstate

    %% 반복 루프
    PushGitHub -.-> NextVol([🔄 Next Volume 기획]):::start
    CopyPaste -.-> NextVol
