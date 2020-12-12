---
description: Progress_reporter 클래스에 대해 자세히 알아보세요.
title: progress_reporter 클래스
ms.date: 11/04/2016
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
ms.openlocfilehash: 40ae3dba0c804381478d8c32da4425b20a9825d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169361"
---
# <a name="progress_reporter-class"></a>progress_reporter 클래스

진행률 보고자 클래스를 사용하면 특정 형식의 진행률 알림을 보고할 수 있습니다. 각 progress_reporter 개체는 특정 비동기 작업이나 연산에 바인딩됩니다.

## <a name="syntax"></a>구문

```cpp
template<typename _ProgressType>
class progress_reporter;
```

### <a name="parameters"></a>매개 변수

*_ProgressType*<br/>
진행률 보고자를 통해 보고되는 각 진행률 알림의 페이로드 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[progress_reporter](#ctor)||

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[report (보고서)](#report)|이 진행률 보고자가 바인딩된 비동기 작업이나 연산에 진행률 보고서를 보냅니다.|

## <a name="remarks"></a>설명

이 형식은 Windows 런타임 앱 에서만 사용할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`progress_reporter`

## <a name="requirements"></a>요구 사항

**헤더:** ppltasks.h

**네임 스페이스:** 동시성

## <a name="progress_reporter"></a><a name="ctor"></a> progress_reporter

```cpp
progress_reporter();
```

## <a name="report"></a><a name="report"></a> 리포트

이 진행률 보고자가 바인딩된 비동기 작업이나 연산에 진행률 보고서를 보냅니다.

```cpp
void report(const _ProgressType& val) const;
```

### <a name="parameters"></a>매개 변수

*짧은*<br/>
진행률 알림을 통해 보고할 페이로드입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
