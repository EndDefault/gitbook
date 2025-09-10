---
title: project
author: 권순규
date: 2024-02-04
category: git
layout: post
mermaid: true
---

[사이트](https://mermaid.js.org/)

```mermaid
flowchart TD
 subgraph 로그인["로그인"]
        Login["로그인"]
        Find["ID/PW 찾기"]
        Mem["회원가입"]
  end
 subgraph 복권["복권"]
        Pay["복권결제"]
        Auto["자동 생성"]
        Passive["수동 선택"]
        Semi-auto["반자동 생성"]
        Auto & Passive & Semi-auto --> Pay
  end
 subgraph 기능
        MP["마이페이지"]
        Bord["게시판"]
        Comment["댓글"]
        Notice["공지사항"]
        FAQ["FAQ"]
  end
 subgraph 나가기["나가기"]
        P["회원탈퇴"]
        Q["로그아웃"]
  end
    Z["들어가기"] --> 로그인
    로그인 -- YES --> Main["메인화면"]
    Login -- NO --> Find & Mem
    Mem & Find --> Login
    Main --> 복권 & Map["지도 판매점"] & win["당첨여부"] & 기능 & Message["1:1 관리자 채팅"] & 나가기
    나가기 --> 로그인
    

    style Z stroke-width:4px,stroke-dasharray: 0,color:#000000,fill:#FFF9C4
    style 로그인 fill:#FFE0B2,color:#000000
    style 복권 fill:#FFE0B2
    style 기능 fill:#FFE0B2
    style 나가기 fill:#FFE0B2
```