---
title: project
author: 권순규
date: 2024-02-04
category: git
layout: post
mermaid: true
---

[사이트](https://mermaid.js.org/)

# 다이어로그
```mermaid
flowchart LR
 subgraph 로그인["로그인"]
        Login["로그인"]
        Find["ID/PW 찾기"]
        Mem["회원가입"]
        text_2(["실패"])
  end
 subgraph 복권["복권"]
        Pay["복권결제"]
        Auto["자동 생성"]
        Passive["수동 선택"]
        Semi-auto["반자동 생성"]
  end
 subgraph 마이페이지["마이페이지"]
        MP["마이페이지"]
        MP_1["구매복권이력"]
        MP_2["마일리지"]
        MP_3["충전금액"]
  end
 subgraph 게시판["게시판"]
        Notice["공지사항"]
        FAQ["FAQ"]
        Bord["게시판"]
  end
 subgraph 나가기["나가기"]
        P["회원탈퇴"]
        Q["로그아웃"]
  end
    Auto --> Pay
    Passive --> Pay
    Semi-auto --> Pay
    MP --> MP_1 & MP_2 & MP_3
    Z["들어가기"] --> Main["메인화면"]
    로그인 --> text_1(["성공"])
    text_1 --> Main
    Login --> text_2
    text_2 --> Find & Mem
    Mem --> Login
    Find --> Login
    Main --> 복권 & Map["지도 판매점"] & win["당첨여부"] & 마이페이지 & Message["1:1 관리자 채팅"] & 나가기 & 게시판
    복권 --> text(["구매"])
    text --> MP_1
    MP_1 --> win
    나가기 --> 로그인
    Comment["댓글"]

    Z@{ shape: dbl-circ}
    Main@{ shape: hex}
     text_2:::hl
     text_1:::hl
     text:::hl
    classDef hl fill:#C8E6C9,stroke:#2E7D32,stroke-width:1px,color:#000
    style Z stroke-width:4px,stroke-dasharray: 0,color:#000000,fill:#FFF9C4
    style 로그인 fill:#FFE0B2,color:#000000
    style 복권 fill:#FFE0B2
    style 마이페이지 fill:#FFE0B2
    style 나가기 fill:#FFE0B2
    style 게시판 fill:#FFE0B2


    %% 스타일 정의(한 번만)
    classDef hl fill:#C8E6C9,stroke:#2E7D32,stroke-width:1px,color:#000;

    %% 여러 노드에 한 번에 적용
    class text,text_1,text_2 hl;
```

# 로그인
```mermaid 
flowchart TD
    in--> text1["회원인가?"]
    text1 --- yes(["yes"]) & no(["no"])
    yes --> login["로그인"] 
    no --> mem["회원가입"]
    mem --> login 
    login <--> find["ID/PW찾기"]
    login --> fin

    in@{ shape: sm-circ}
    text1@{ shape: diam}
    fin@{ shape: f-circ}

    classDef Check fill:#C8E6C9
    class yes,no Check;
    style in fill:#FFD600
```

# database
```erDiagram
direction TB
	회원가입{
		string ID  "pk" 
		String pw  "not null"  
		String nickname  "not null"  
		string name  "not null"  
		string email  "not null"  
	}
	회원 {
		string ID  "pk" 
    	String pw  "not null"  
		String nickname  "not null"  
		string name  "not null"  
		string email  "not null"  
        int pay "defualt : 0"
        int ticket "defualt : 0"
        boolean admin "defualt : false"
	}
    복권{
        String ID "pk"
        String ticket "not null"
        INT round "fk(당첨)"
    }
    당첨{
        INT round "PK, fk"
        int num1 
        int num2
        int num3 
        int num4 
        int num5 
        int bonus 
    }
    게시판{
        String ID "pk"
        String nickname ""
    }

	회원가입||--||회원:"가입"
    회원||--o{복권:"구매"
    당첨||--o{복권:"확인"
    회원||--o{게시판:"창작"
```