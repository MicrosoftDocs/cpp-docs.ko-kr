---
description: '자세한 내용은 _com_error:: _com_error을 (를) 확인 하세요.'
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 2c5b912f5d532e9aed5b8e84a3fe7e2fcd7d4100
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332563"
---
# <a name="_com_error_com_error"></a>_com_error::_com_error

**Microsoft 전용**

**_Com_error** 개체를 생성 합니다.

## <a name="syntax"></a>구문

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>매개 변수

*시간*<br/>
HRESULT 정보입니다.

*perrinfo*<br/>
`IErrorInfo` 개체입니다.

*fAddRef*<br/>
기본값을 설정 하면 생성자가 null이 아닌 인터페이스에서 AddRef를 호출 합니다 `IErrorInfo` . 이렇게 하면 인터페이스의 소유권이 **_com_error** 개체로 전달 되는 일반적인 경우에 올바른 참조 횟수를 얻을 수 있습니다. 예를 들면 다음과 같습니다.

```cpp
throw _com_error(hr, perrinfo);
```

코드가 **_com_error** 개체에 소유권을 양도 하지 않도록 하 고 `AddRef` _com_error 소멸자에서를 오프셋 하기 위해가 필요한 경우 다음과 `Release` 같이 개체  를 생성 합니다.

```cpp
_com_error err(hr, perrinfo, true);
```

*that*<br/>
기존 **_com_error** 개체입니다.

## <a name="remarks"></a>설명

첫 번째 생성자는 HRESULT 및 선택적 개체가 지정 된 경우 새 개체를 만듭니다 `IErrorInfo` . 두 번째는 기존 **_com_error** 개체의 복사본을 만듭니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error 클래스](../cpp/com-error-class.md)
