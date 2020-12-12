---
description: _Com_ptr_t 클래스에 대해 자세히 알아보세요.
title: _com_ptr_t 클래스
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
ms.openlocfilehash: a68b522806cec14baffe7857c71ac171ed0407f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295616"
---
# <a name="_com_ptr_t-class"></a>_com_ptr_t 클래스

**Microsoft 전용**

**_Com_ptr_t** 개체는 com 인터페이스 포인터를 캡슐화 하 고 "스마트" 포인터 라고 합니다. 이 템플릿 클래스는 `IUnknown` , 및 멤버 함수에 대 한 함수 호출을 통해 리소스 할당 및 할당 취소를 관리 `QueryInterface` `AddRef` `Release` 합니다.

스마트 포인터는 일반적으로 _COM_SMARTPTR_TYPEDEF 매크로가 제공하는 typedef 정의에서 참조됩니다. 이 매크로는 인터페이스 이름과 IID를 사용 하 고 인터페이스 이름과의 접미사를 사용 하 여 **_com_ptr_t** 의 특수화를 선언 합니다 `Ptr` . 예를 들어:

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

**_com_ptr_t** 특수화를 선언 `IMyInterfacePtr` 합니다.

이 템플릿 클래스의 멤버가 아닌 [함수 템플릿](../cpp/relational-function-templates.md)집합은 비교 연산자의 오른쪽에 있는 스마트 포인터를 사용한 비교를 지원 합니다.

### <a name="construction"></a>건설

| Name | 설명 |
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|**_Com_ptr_t** 개체를 생성 합니다.|

### <a name="low-level-operations"></a>하위 수준 연산

| Name | 설명 |
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|`AddRef` `IUnknown` 캡슐화 된 인터페이스 포인터에 대 한의 멤버 함수를 호출 합니다.|
|[연결](../cpp/com-ptr-t-attach.md)|이 스마트 포인터 형식의 원시 인터페이스 포인터를 캡슐화합니다.|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|또는를 지정 하 여 개체의 새 인스턴스를 만듭니다 `CLSID` `ProgID` .|
|[분리](../cpp/com-ptr-t-detach.md)|캡슐화된 인터페이스 포인터를 추출하고 반환합니다.|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|또는가 지정 된 개체의 기존 인스턴스에 연결 `CLSID` `ProgID` 합니다.|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|캡슐화된 인터페이스 포인터가 반환됩니다.|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|`QueryInterface` `IUnknown` 캡슐화 된 인터페이스 포인터에 대 한의 멤버 함수를 호출 합니다.|
|[릴리스](../cpp/com-ptr-t-release.md)|`Release` `IUnknown` 캡슐화 된 인터페이스 포인터에 대 한의 멤버 함수를 호출 합니다.|

### <a name="operators"></a>연산자

| Name | 설명 |
|-|-|
|[연산자 =](../cpp/com-ptr-t-operator-equal.md)|기존 **_com_ptr_t** 개체에 새 값을 할당 합니다.|
|[연산자 = =,! =, \<, > , \<=, >=](../cpp/com-ptr-t-relational-operators.md)|스마트 포인터 개체를 다른 스마트 포인터, 원시 인터페이스 포인터 또는 NULL과 비교합니다.|
|[추출기](../cpp/com-ptr-t-extractors.md)|캡슐화된 COM 인터페이스 포인터를 추출합니다.|

**Microsoft 전용 종료**

## <a name="requirements"></a>요구 사항

**헤더:**\<comip.h>

**Lib:** comsuppw 또는 comsuppw .lib (자세한 내용은 [/zc: Wchar_t (wchar_t 네이티브 형식)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 참조)

## <a name="see-also"></a>참고 항목

[컴파일러 COM 지원 클래스](../cpp/compiler-com-support-classes.md)
