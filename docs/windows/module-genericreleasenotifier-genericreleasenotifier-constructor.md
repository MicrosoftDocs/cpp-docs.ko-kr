---
title: Module::GenericReleaseNotifier::GenericReleaseNotifier 생성자 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier, constructor
ms.assetid: feb5b687-a4b0-4809-9022-8f292181b7a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98bcc3d3fcaf7aea3b2632cacb1ff38eedb868b8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612314"
---
# <a name="modulegenericreleasenotifiergenericreleasenotifier-constructor"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier 생성자

새 인스턴스를 초기화 합니다 **module:: genericreleasenotifier** 클래스입니다.

## <a name="syntax"></a>구문

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>매개 변수

*콜백*  
람다, 함수 또는 괄호 함수 연산자를 사용 하 여 호출할 수 있는 함수에 대 한 포인터 이벤트 처리기 (`()`).

*release*  
지정할 **true** 내부 호출을 사용 하도록 설정 하려면 [모듈:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) 메서드를 지정이 고, 그렇지 **false**합니다.

## <a name="requirements"></a>요구 사항

**헤더:** module.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Module::GenericReleaseNotifier 클래스](../windows/module-genericreleasenotifier-class.md)