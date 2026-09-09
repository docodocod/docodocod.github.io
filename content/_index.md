---
# Leave the homepage title empty to use the site title
title: ''
summary: ''
date: 2026-09-09
type: landing

sections:
  # Developer Hero
  - block: dev-hero
    id: hero
    content:
      username: me
      greeting: "안녕하세요,"
      show_status: true
      show_scroll_indicator: true
      typewriter:
        enable: true
        prefix: "저는"
        strings:
          - "요청 흐름을 분석해 병목을 찾습니다"
          - "동시성과 성능 문제를 구조적으로 개선합니다"
          - "비동기·분산 파이프라인을 설계합니다"
          - "측정과 테스트로 개선 효과를 검증합니다"
        type_speed: 70
        delete_speed: 40
        pause_time: 2500
      cta_buttons:
        - text: 프로젝트 보기
          url: "#projects"
          icon: arrow-down
        - text: 연락하기
          url: "#contact"
          icon: envelope
    design:
      style: centered
      avatar_shape: circle
      animations: true
      background:
        color:
          light: "#fafafa"
          dark: "#0a0a0f"
      spacing:
        padding: ["1.5rem", "0", "3rem", "0"]

  # Filterable Portfolio
  - block: portfolio
    id: projects
    content:
      title: "Projects"
      subtitle: "문제를 정의하고, 원인을 분석하고, 개선 효과를 수치로 검증한 작업들"
      count: 0
      filters:
        folders:
          - projects
      buttons:
        - name: All
          tag: '*'
        - name: Backend
          tag: Backend
        - name: Performance
          tag: Performance
        - name: AI/Data
          tag: AI/Data
      default_button_index: 0
    design:
      # lg 에서 3열. 2로 두면 카드가 넓어집니다.
      # 이미지 칸 비율(3:2)은 assets/css/custom.css 에서 맞춥니다.
      columns: 3
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]

  # Visual Tech Stack
  - block: tech-stack
    id: skills
    content:
      title: "Tech Stack"
      subtitle: "실제 프로젝트와 업무에서 사용한 기술들"
      categories:
        - name: Languages
          items:
            - name: Java
              icon: devicon/java
            - name: Python
              icon: devicon/python
            - name: JavaScript
              icon: devicon/javascript
        - name: Frameworks
          items:
            - name: Spring Boot
              icon: devicon/spring
            - name: FastAPI
              icon: devicon/fastapi
        - name: Databases & MQ
          items:
            - name: PostgreSQL
              icon: devicon/postgresql
            - name: MySQL
              icon: devicon/mysql
            - name: Neo4j
              icon: devicon/neo4j
            - name: Redis
              icon: devicon/redis
            - name: RabbitMQ
              icon: devicon/rabbitmq
            - name: Kafka
              icon: devicon/apachekafka
        - name: Infra & DevOps
          items:
            - name: Docker
              icon: devicon/docker
            - name: Nginx
              icon: devicon/nginx
            - name: GitHub Actions
              icon: devicon/githubactions
            - name: AWS
              icon: devicon/amazonwebservices
            - name: GCP
              icon: devicon/googlecloud
    design:
      style: grid
      show_levels: false
      background:
        color:
          light: "#f5f5f5"
          dark: "#08080c"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]

  # Experience Timeline
  # 주의: 이 블록은 content.items 를 읽지 않습니다.
  #       Experience/Education 내용은 전부 data/authors/me.yaml 에서 가져옵니다.
  #       (제목도 테마의 i18n 값으로 고정되어 content.title 이 적용되지 않습니다.)
  - block: resume-experience
    id: experience
    content:
      username: me
    design:
      date_format: 2006.01
      is_education_first: false
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]

  # Activities (Experience 와 동일한 타임라인 디자인 - 커스텀 timeline 블록)
  - block: timeline
    id: activities
    content:
      title: Activities
      text: 팀과 함께한 프로젝트, 스터디, 그리고 커뮤니티 활동입니다.
      items:
        - title: 스마트해운물류 x ICT 멘토링 프로젝트
          org: 한국정보산업연합회 주관
          date: "2026.05 ~ 진행 중"
          icon: hero/trophy
          summary: |-
            시니어 멘토 지도하에 울산항 액체화물 안전 관제 시스템을 기획·개발했습니다.
            3인 팀에서 AI 파트를 담당했고, 주간 멘토링을 통해 아키텍처 방향을 수정하고
            기술 의사결정을 경험했습니다. 현재 50팀 중 14팀에 들어 예선을 통과했습니다.
          tags:
            - 예선 통과
            - AI 파트
        - title: Techeer[테커] 10기
          org: 실리콘밸리 개발자 네트워크 기반 커리어 그룹
          date: "2025.08 ~ 진행 중"
          icon: hero/user-group
          summary: |-
            팀 기술 스터디와 팀 프로젝트에 참여했습니다.
        - title: Techeer Silicon Valley SW Bootcamp
          org: 팀장
          date: "2025.07 ~ 2025.08"
          icon: hero/rocket-launch
          summary: |-
            팀장으로 AI 뉴스 브리핑 서비스를 개발했습니다.
            데일리 스크럼을 운영하고 백엔드 파이프라인 전반을 주도했습니다.
          tags:
            - 팀장
            - 백엔드 리드
        - title: 교내 개발 동아리 씨부엉
          org: 한국공학대학교
          date: "2025.03 ~ 2026.08"
          icon: hero/code-bracket
          summary: |-
            백엔드/웹 기술 자율 스터디에 참여하고,
            동아리 자체 플랫폼 웹 서비스 개발 프로젝트에 참여했습니다.
        - title: 로타랙트 봉사 활동
          org: 임원
          date: "2025.03 ~ 2026.08"
          icon: hero/heart
          summary: |-
            월 정기 봉사 일정을 기획·운영하고,
            복지관 도시락 배달과 지역 행사 봉사를 주도했습니다.
    design:
      color: primary
      background:
        color:
          light: "#f5f5f5"
          dark: "#08080c"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]

  # Certifications (Education 과 동일한 secondary 색 타임라인)
  # 취득일 최신순. 자격증 번호는 개인 식별 정보라 공개 사이트에 넣지 않았습니다.
  - block: timeline
    id: certifications
    content:
      title: Certifications
      items:
        - title: ADsP (데이터분석 준전문가)
          org: 한국데이터산업진흥원
          date: "2026.06"
          icon: hero/chart-bar
        - title: TOPCIT Lv3
          org: 정보통신기획평가원
          date: "2026.06"
          icon: hero/academic-cap
        - title: 정보처리기사
          org: 한국산업인력공단
          date: "2024.06"
          icon: hero/check-badge
        - title: SQLD (SQL 개발자)
          org: 한국데이터산업진흥원
          date: "2023.04"
          icon: hero/circle-stack
        - title: 컴퓨터활용능력 1급
          org: 대한상공회의소
          date: "2019.10"
          icon: hero/table-cells
        - title: 정보처리산업기사
          org: 한국산업인력공단
          date: "2018.11"
          icon: hero/check-badge
        - title: 네트워크관리사 2급
          org: 한국정보통신자격협회
          date: "2016.09"
          icon: hero/server-stack
    design:
      color: secondary
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]

  # Contact Section
  - block: contact-info
    id: contact
    content:
      title: Contact
      subtitle: "제안이나 궁금한 점이 있다면 편하게 연락 주세요"
      text: |-
        백엔드 포지션 제안, 프로젝트 협업, 기술적인 이야기 모두 환영합니다.
        메일로 연락 주시면 확인 후 답장드리겠습니다.
      email: dongan0618@naver.com
      autolink: true
    design:
      columns: '1'
      background:
        color:
          light: "#f5f5f5"
          dark: "#08080c"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]

  # CTA Card
  - block: cta-card
    content:
      title: "함께 일할 기회를 찾고 있습니다"
      text: |-
        2027년 2월 졸업 예정으로, **백엔드 엔지니어** 포지션을 찾고 있습니다.

        이력서에서 각 프로젝트의 문제 정의와 개선 과정을 더 자세히 보실 수 있습니다.
      button:
        text: '이력서 다운로드'
        url: uploads/resume.pdf
        new_tab: true
    design:
      card:
        css_class: 'bg-gradient-to-br from-primary-200 via-primary-100 to-secondary-200 dark:from-primary-600 dark:via-primary-700 dark:to-secondary-700'
        text_color: dark
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "6rem", "0"]
---
