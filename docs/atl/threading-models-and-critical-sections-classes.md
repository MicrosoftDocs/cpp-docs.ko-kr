---
description: '자세한 정보: 스레딩 모델 및 임계 영역 클래스'
title: 스레딩 모델 및 임계 영역 클래스 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
ms.openlocfilehash: 51ad5a5f2f03bfe080395966d0c480615c49a109
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138283"
---
# <a name="threading-models-and-critical-sections-classes"></a>스레딩 모델 및 임계 영역 클래스

다음 클래스는 스레딩 모델 및 임계 영역을 정의 합니다.

- [Catlautothreadmodule](../atl/reference/catlautothreadmodule-class.md) 스레드 풀의 아파트 모델 COM 서버를 구현 합니다.

- [Catlautothreadmodulet](../atl/reference/catlautothreadmodulet-class.md) 스레드 풀의 아파트 모델 COM 서버를 구현 하는 메서드를 제공 합니다.

- [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) 변수를 증가 및 감소 시키는 스레드로부터 안전한 메서드를 제공 합니다. 임계 영역을 제공 합니다.

- [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) 변수를 증가 및 감소 시키는 스레드로부터 안전한 메서드를 제공 합니다. 는 임계 영역을 제공 하지 않습니다.

- [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) 변수를 증가 및 감소 시키는 메서드를 제공 합니다. 는 임계 영역을 제공 하지 않습니다.

- [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) 단일 개체 클래스에 대 한 적절 한 스레딩 모델 클래스를 결정 합니다.

- [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel) 전역적으로 사용할 수 있는 개체에 대 한 적절 한 스레딩 모델 클래스를 결정 합니다.

- [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) 임계 영역을 가져오고 해제 하기 위한 메서드를 포함 합니다. 임계 섹션이 자동으로 초기화 됩니다.

- [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) 임계 영역을 가져오고 해제 하기 위한 메서드를 포함 합니다. 임계 영역을 명시적으로 초기화 해야 합니다.

- [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) `CComCriticalSection` 임계 영역을 제공 하지 않고의 메서드를 미러링합니다. 의 메서드는 `CComFakeCriticalSection` 아무 작업도 수행 하지 않습니다.

- [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) CRT 스레드에 대 한 생성 함수를 제공 합니다. 스레드에서 CRT 함수를 사용 하는 경우이 클래스를 사용 합니다.

- [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) Windows 스레드에 대 한 생성 함수를 제공 합니다. 스레드에서 CRT 함수를 사용 하지 않는 경우이 클래스를 사용 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../atl/atl-class-overview.md)
