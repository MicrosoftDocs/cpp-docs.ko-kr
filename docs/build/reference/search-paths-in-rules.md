---
description: '자세히 알아보기: 규칙에서 경로 검색'
title: 규칙에서 경로 검색
ms.date: 11/04/2016
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
ms.openlocfilehash: bf070fc57907b68eb458b8a5276698282ef30f9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224883"
---
# <a name="search-paths-in-rules"></a>규칙에서 경로 검색

```
{frompath}.fromext{topath}.toext:
   commands
```

## <a name="remarks"></a>설명

유추 규칙은 종속성에 지정 된 경로가 유추 규칙 경로와 정확히 일치 하는 경우에만 종속성에 적용 됩니다. *Topath*;의 *frompath* 및 대상 디렉터리에 종속 디렉터리를 지정 합니다. 공백은 허용 되지 않습니다. 각 확장에 대해 하나의 경로만 지정 합니다. 한 확장의 경로에 다른 경로에 대 한 경로가 필요 합니다. 현재 디렉터리를 지정 하려면 마침표 (.) 또는 빈 중괄호 ({}) 중 하나를 사용 합니다. 매크로는 *frompath* 및 *topath* 을 나타낼 수 있습니다. 전처리 하는 동안 호출 됩니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

```
{dbi\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUDBI) $<

{ilstore\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{misc\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{misc\}.c{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{msf\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{bsc\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{mre\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{namesrvr\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{src\cvr\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<
```

## <a name="see-also"></a>참조

[규칙 정의](defining-a-rule.md)
