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
 subgraph 로그인["회원인가?"]
        Login["로그인"]
        non(["비회원"])
        Find["ID/PW 찾기"]
        Mem["회원가입"]
        y_mem(["회원"])
        non --> Mem --> Login
        y_mem --> Login
        Login <--> Find
  end
 subgraph 복권["복권"]
        Pay["복권결제"]
        Auto["자동 생성"]
        Passive["수동 선택"]
        Semi-auto["반자동 생성"]
        Auto & Passive & Semi-auto --> Pay
  end
 subgraph 마이페이지["마이페이지"]
        MP["마이페이지"]
        MP_1["구매복권이력"]
        MP_2["마일리지"]
        MP_3["충전금액"]
        MP --> MP_1 & MP_2 & MP_3
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
    
    Z --> Main["메인화면"]
    Main --> 로그인


    Comment["댓글"]

    Z@{ shape: sm-circ}
    Main@{ shape: hex}
 

    style Z stroke-width:4px,stroke-dasharray: 0,color:#000000,fill:#FFF9C4

    %% 스타일 정의(한 번만)
    classDef check fill:#C8E6C9,stroke:#2E7D32,stroke-width:1px,color:#000;
    classDef col fill:#FFE0B2,font-size:30px;

    %% 여러 노드에 한 번에 적용
    class text,text_1,y_mem,non check;
    class 로그인,복권,마이페이지,나가기,게시판 col;
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
```mermaid
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