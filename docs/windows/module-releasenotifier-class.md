---
title: "Module:: releasenotifier 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier class
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb640f146109363a8025818b3ec560c250029914
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier 클래스
모듈의 마지막 개체가 해제될 때 이벤트 처리기를 호출합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[Module::ReleaseNotifier::~ReleaseNotifier 소멸자](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|Module::ReleaseNotifier 클래스의 현재 인스턴스 초기화를 취소합니다.|  
|[Module::ReleaseNotifier::ReleaseNotifier 생성자](../windows/module-releasenotifier-releasenotifier-constructor.md)|Module::ReleaseNotifier 클래스의 새 인스턴스를 초기화합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke 메서드](../windows/module-releasenotifier-invoke-method.md)|구현될 때 모듈의 마지막 개체가 해제되면 이벤트 처리기를 호출합니다.|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|`true`의 매개 변수로 개체를 생성한 경우 현재 Module::ReleaseNotifier 개체를 삭제합니다.|  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** module.h  
  
 **네임스페이스:** Microsoft::WRL
 
 ## <a name="see-also"></a>참고 항목
 [Module 클래스](../windows/module-class.md)