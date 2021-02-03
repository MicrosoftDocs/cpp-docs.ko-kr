---
title: _bstr_t 클래스
description: _Bstr_t 클래스에 대해 자세히 알아보세요.
ms.date: 02/02/2021
f1_keywords:
- _bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.openlocfilehash: 71f5f0a27989b416cf4f13873254890db09ce334
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522874"
---
# <a name="_bstr_t-class"></a>`_bstr_t` 클래스

**Microsoft 전용**

`_bstr_t`개체는 [BSTR 데이터 형식을](/previous-versions/windows/desktop/automat/bstr)캡슐화 합니다. 클래스는 [`SysAllocString`](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) [`SysFreeString`](/windows/win32/api/oleauto/nf-oleauto-sysfreestring) 적절 한 경우 및 및 기타 api에 대 한 함수 호출을 통해 리소스 할당 및 할당 취소를 관리 합니다 `BSTR` . `_bstr_t`클래스는 과도 한 오버 헤드를 방지 하기 위해 참조 횟수를 사용 합니다.

## <a name="members"></a>멤버

### <a name="construction"></a>건설

| 생성자 | Description |
|--|--|
| [`_bstr_t`](../cpp/bstr-t-bstr-t.md) | `_bstr_t` 개체를 생성합니다. |

### <a name="operations"></a>작업

| 기능 | 설명 |
|--|--|
| [`Assign`](../cpp/bstr-t-assign.md) | `BSTR`을 `BSTR`로 래핑된 `_bstr_t`로 복사합니다. |
| [`Attach`](../cpp/bstr-t-attach.md) | `_bstr_t` 래퍼를 `BSTR`에 연결합니다. |
| [`copy`](../cpp/bstr-t-copy.md) | 캡슐화된 `BSTR`의 복사본을 구성합니다. |
| [`Detach`](../cpp/bstr-t-detach.md) | `BSTR`로 래핑된 `_bstr_t`을 반환하고 `BSTR`을 `_bstr_t`에서 분리합니다. |
| [`GetAddress`](../cpp/bstr-t-getaddress.md) | `BSTR`로 래핑된 `_bstr_t`을 가리킵니다. |
| [`GetBSTR`](../cpp/bstr-t-getbstr.md) | `BSTR`에 의해 래핑되는 `_bstr_t`의 시작 부분을 가리킵니다. |
| [`length`](../cpp/bstr-t-length.md) | `_bstr_t`에 있는 문자의 수를 반환합니다. |

### <a name="operators"></a>연산자

| 연산자 | 설명 |
|--|--|
| [`operator =`](../cpp/bstr-t-operator-equal.md) | 기존 `_bstr_t` 개체에 새 값을 할당합니다. |
| [`operator +=`](../cpp/bstr-t-operator-add-equal-plus.md) | `_bstr_t` 개체의 끝 부분에 문자를 추가합니다. |
| [`operator +`](../cpp/bstr-t-operator-add-equal-plus.md) | 두 문자열을 연결합니다. |
| [`operator !`](../cpp/bstr-t-operator-logical-not.md) | 캡슐화 된이 NULL 문자열 인지 여부를 확인 합니다 `BSTR` . |
| [`operator ==`](../cpp/bstr-t-relational-operators.md)<br/>[`operator !=`](../cpp/bstr-t-relational-operators.md)<br/>[`operator <`](../cpp/bstr-t-relational-operators.md)<br/>[`operator >`](../cpp/bstr-t-relational-operators.md)<br/>[`operator <=`](../cpp/bstr-t-relational-operators.md)<br/>[`operator >=`](../cpp/bstr-t-relational-operators.md) | 두 개의 `_bstr_t` 개체를 비교합니다. |
| [`operator wchar_t*`](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)<br/>[`operator char*`](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)  | 캡슐화된 유니코드 또는 멀티바이트 `BSTR` 개체에 대한 포인터를 추출합니다. |

**Microsoft 전용 종료**

## <a name="requirements"></a>요구 사항

**헤더:**\<comutil.h>

**Lib:** *`comsuppw.lib`* ( *`comsuppwd.lib`* 자세한 내용은 [ `/Zc:wchar_t` (wchar_t 네이티브 형식)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 COM 지원 클래스](../cpp/compiler-com-support-classes.md)
