---
title: test
author: 권순규
date: 2024-02-04
category: git
layout: post
mermaid: true
---

```mermaid
flowchart TD
     A["로그인"] -- YES --> B["메인화면"]
    A -- NO --> D["회원가입"] & C["ID/PW 찾기"]
    C --> B
    D --> B
    B --> E["복권결제"] & F["지도 판매점"] & G["당첨여부"] & Q["마이페이지"] & O["1:1 관리자 채팅"] & P["회원탈퇴"]
    E --> H["자동 생성"] & I["수동 선택"] & J["반자동 생성"]
    Q --> K["게시판"] & L["댓글"] & M["공지사항"] & N["FAQ"]
```
