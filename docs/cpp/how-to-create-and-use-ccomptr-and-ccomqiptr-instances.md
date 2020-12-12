---
description: '자세한 정보: 방법: CComPtr 및 CComQIPtr 인스턴스 만들기 및 사용'
title: '방법: CComPtr 및 CComQIPtr 인스턴스 만들기 및 사용'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: c16d908e3df9e10641f1264aed7623463424de69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268654"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>방법: CComPtr 및 CComQIPtr 인스턴스 만들기 및 사용

클래식 Windows 프로그래밍에서 라이브러리는 종종 COM 개체(보다 정확하게는 COM 서버)로 구현됩니다. 많은 Windows 운영 체제 구성 요소가 COM 서버로 구현되므로 많은 참가자가 이 형식의 라이브러리를 제공합니다. COM의 기본 사항에 대한 자세한 내용은 [Component Object Model (COM)](/windows/win32/com/component-object-model--com--portal)을 참조하세요.

COM(구성 요소 개체 모델) 개체를 인스턴스화할 때 소멸자에서 `AddRef` 및 `Release` 에 대한 호출을 사용하여 참조 계산을 수행하는 COM 스마트 포인터에 인터페이스 포인터를 저장합니다. ATL(액티브 템플릿 라이브러리) 또는 MFC 라이브러리를 사용하는 경우 `CComPtr` 스마트 포인터를 사용합니다. ATL 또는 MFC를 사용하지 않는 경우에는 `_com_ptr_t`를 사용합니다. `std::unique_ptr`에 해당하는 COM이 없기 때문에 단일 소유자 시나리오와 여러 소유자 시나리오 모두에 이러한 스마트 포인터를 사용합니다. `CComPtr` 과 `ComQIPtr` 둘 다 rvalue 참조가 있는 이동 작업을 지원합니다.

## <a name="example-ccomptr"></a>예: CComPtr

다음 예제에서는 `CComPtr` 을 사용하여 COM 개체를 인스턴스화하고 해당 인터페이스에 대한 포인터를 가져오는 방법을 보여 줍니다. `CComPtr::CoCreateInstance` 멤버 함수는 이름이 같은 Win32 함수 대신 COM 개체를 만드는 데 사용됩니다.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` 및 해당 친척은 ATL의 일부 이며에 정의 되어 \<atlcomcli.h> 있습니다. `_com_ptr_t` 는에서 선언 됩니다 \<comip.h> . 컴파일러는 형식 라이브러리에 대한 래퍼 클래스를 생성할 때 `_com_ptr_t` 의 특수화를 만듭니다.

## <a name="example-ccomqipt"></a>예: CComQIPt

또한 ATL은 COM 개체를 쿼리하여 추가 인터페이스를 검색할 수 있도록 보다 간단한 구문이 있는 `CComQIPtr`을 제공합니다. 그러나 `CComPtr` 에서 수행할 수 있는 모든 작업을 수행하고 원시 COM 인터페이스 포인터와 의미 체계가 보다 일치하므로 `CComQIPtr` 을 사용하는 것이 좋습니다. `CComPtr` 를 사용하여 인터페이스를 쿼리하는 경우 out 매개 변수에 새 인터페이스 포인터가 배치됩니다. 호출에 실패한 경우 일반적인 COM 패턴인 HRESULT가 반환됩니다. `CComQIPtr`을 사용하는 경우 반환 값은 포인터 자체이며, 호출에 실패한 경우 내부 HRESULT 반환 값에 액세스할 수 없습니다. 다음 두 줄은 `CComPtr` 과 `CComQIPtr` 의 오류 처리 메커니즘 차이를 보여 줍니다.

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example-idispatch"></a>예: IDispatch

`CComPtr` 은 COM 자동화 구성 요소에 대한 포인터를 저장하고 런타임에 바인딩을 사용하여 인터페이스에서 메서드를 호출할 수 있도록 하는 IDispatch 특수화를 제공합니다. `CComDispatchDriver` 는 암시적으로 `CComQIPtr<IDispatch, &IIDIDispatch>`로 변환할 수 있는 `CComPtr<IDispatch>`에 대한 typedef입니다. 따라서 이 세 가지 이름 중 하나가 코드에 표시되면 이는 `CComPtr<IDispatch>`와 같습니다. 다음 예제에서는 `CComPtr<IDispatch>`를 사용하여 Microsoft Word 개체 모델에 대한 포인터를 가져오는 방법을 보여 줍니다.

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>참고 항목

[스마트 포인터 (최신 c + +)](../cpp/smart-pointers-modern-cpp.md)
