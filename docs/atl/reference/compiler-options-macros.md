---
description: '자세한 정보: 컴파일러 옵션 매크로'
title: 컴파일러 옵션 매크로
ms.date: 08/19/2019
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
ms.openlocfilehash: 247ede37721d868c9c941ce85e024a55a2487947
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141273"
---
# <a name="compiler-options-macros"></a>컴파일러 옵션 매크로

이러한 매크로는 특정 컴파일러 기능을 제어 합니다.

|매크로|설명|
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|이전 버전의 ATL에서 변환 된 프로젝트에서 오류를 사용 하도록 설정 하는 기호입니다.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|하나 이상의 개체가 아파트 스레딩을 사용 하는지 여부를 정의 합니다.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|특정 `CString` 생성자를 명시적으로 만들어 의도 하지 않은 변환을 방지 합니다.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|비-표준 구문을 사용 하 여 멤버 함수에 대 한 포인터를 초기화할 때 C4867 컴파일러 오류를 생성 하는 c + + 표준 규격 구문을 사용 하기 위해이 매크로를 정의 합니다.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|하나 이상의 개체가 자유 또는 중립 스레딩을 사용 하는지 여부를 정의 합니다.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|프로젝트에 사용 가능 또는 중립으로 표시 되는 개체를 나타내는 기호입니다. 대신 매크로 [_ATL_FREE_THREADED](#_atl_free_threaded) 를 사용 해야 합니다.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|기본 네임 스페이스를 ATL로 사용할 수 없도록 하는 기호입니다.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|COM 관련 코드가 프로젝트를 사용 하 여 컴파일되지 않도록 하는 기호입니다.|
|[ATL_NO_VTABLE](#atl_no_vtable)|클래스의 생성자와 소멸자에서 vtable 포인터가 초기화 되지 않도록 하는 기호입니다.|
|[ATL_NOINLINE](#atl_noinline)|함수를 인라이닝 하지 않아야 함을 나타내는 기호입니다.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|모든 개체가 단일 스레딩 모델을 사용 하는지 여부를 정의 합니다.|

## <a name="_atl_all_warnings"></a><a name="_atl_all_warnings"></a> _ATL_ALL_WARNINGS

이전 버전의 ATL에서 변환 된 프로젝트에서 오류를 사용 하도록 설정 하는 기호입니다.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>설명

.NET 2002을 Visual C++ 하기 전에는 ATL에서 많은 경고를 사용 하지 않도록 설정 하 고 사용 하지 않도록 설정 하 여 사용자 코드에 표시 되지 않도록 합니다. 특히 다음 사항에 주의하세요.

- C4127 조건식이 상수입니다.

- C4786 ' identifier ': 식별자가 디버그 정보에서 ' number ' 자로 잘렸습니다.

- C4201 비표준 확장이 사용 됨: 이름이 없는 구조체/공용 구조체

- C4103 ' filename ': #pragma 팩을 사용 하 여 맞춤을 변경 합니다.

- C4291 ' 선언 ': 일치 하는 operator delete를 찾을 수 없습니다. 초기화에서 예외가 throw 되 면 메모리가 해제 되지 않습니다.

- C4268 ' identifier ': 컴파일러에서 생성 된 기본 생성자를 사용 하 여 초기화 된 ' const ' 정적/전역 데이터는 개체를 0으로 채웁니다.

- C4702 접근할 수 없는 코드

이전 버전에서 변환 된 프로젝트에서는 라이브러리 헤더에 의해 이러한 경고가 계속 비활성화 됩니다.

라이브러리 헤더를 포함 하기 전에 *.pch* (Visual Studio 2017이 하 버전의 *stdafx.h* ) 파일에 다음 줄을 추가 하 여이 동작을 변경할 수 있습니다.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

이를 추가 하는 경우 `#define` ATL 헤더는 이러한 경고의 상태를 전역적으로 사용 하지 않도록 설정 하는 데 주의를 기울여야 합니다. 즉, 사용자가 개별 경고를 사용 하도록 설정 하지 않고 명시적으로 사용 하지 않도록 설정 합니다.

새 프로젝트에는 `#define` 기본적으로이 집합이 *.pch. h* (Visual Studio 2017 및 이전 버전의 *stdafx.h* )에 있습니다.

## <a name="_atl_apartment_threaded"></a><a name="_atl_apartment_threaded"></a> _ATL_APARTMENT_THREADED

하나 이상의 개체가 아파트 스레딩을 사용 하는지 여부를 정의 합니다.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>설명

아파트 스레딩을 지정 합니다. ATL 개체에 사용할 수 있는 스레딩 모델에 대 한 설명은 다른 스레딩 옵션에 대 한 [프로젝트의 스레딩 모델 지정](../../atl/specifying-the-threading-model-for-a-project-atl.md) 및 [옵션, Atl 단순 개체 마법사](../../atl/reference/options-atl-simple-object-wizard.md) 지정을 참조 하세요.

## <a name="_atl_cstring_explicit_constructors"></a><a name="_atl_cstring_explicit_constructors"></a> _ATL_CSTRING_EXPLICIT_CONSTRUCTORS

특정 `CString` 생성자를 명시적으로 만들어 의도 하지 않은 변환을 방지 합니다.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>설명

이 생성자가 정의 되 면 단일 매개 변수를 사용 하는 모든 CString 생성자는 명시적 키워드를 사용 하 여 컴파일되므로 입력 인수를 암시적으로 변환할 수 없습니다. 예를 들어 _UNICODE 정의 된 경우 char * 문자열을 CString 생성자 인수로 사용 하려고 하면 컴파일러 오류가 발생 합니다. 좁은 문자열과 와이드 문자열 형식 간의 암시적 변환을 방지 해야 하는 경우이 매크로를 사용 합니다.

모든 생성자 문자열 인수에서 _T 매크로를 사용 하 여 _ATL_CSTRING_EXPLICIT_CONSTRUCTORS 정의 하 고 _UNICODE 정의 여부에 관계 없이 컴파일 오류를 방지할 수 있습니다.

## <a name="_atl_enable_ptm_warning"></a><a name="_atl_enable_ptm_warning"></a> _ATL_ENABLE_PTM_WARNING

멤버 함수에 대 한 포인터에 ANSI c + + 표준 규격 구문을 강제로 사용 하려면이 매크로를 정의 합니다. 이 매크로를 사용 하면 비표준 구문이 멤버 함수에 대 한 포인터를 초기화 하는 데 사용 될 때 C4867 컴파일러 오류가 생성 됩니다.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>설명

ATL 및 MFC 라이브러리는 Microsoft c + + 컴파일러의 향상 된 표준 c + + 준수와 일치 하도록 변경 되었습니다. ANSI c + + 표준에 따라 클래스 멤버 함수에 대 한 포인터의 구문은 이어야 합니다 `&CMyClass::MyFunc` .

[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) 정의 되지 않은 경우 (기본 경우) ATL/MFC는 매크로 맵 (특히 메시지 맵)에서 C4867 오류를 사용 하지 않도록 설정 하 여 이전 버전에서 만든 코드를 이전과 같이 계속 빌드할 수 있습니다. **_ATL_ENABLE_PTM_WARNING** 를 정의 하는 경우 코드는 c + + 표준 규격 이어야 합니다.

그러나 비표준 폼은 더 이상 사용 되지 않습니다. 기존 코드를 c + + 표준 규격 구문으로 이동 해야 합니다. 예를 들어, 다음 코드는

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

다음으로 변경되어야 합니다.

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

지도 매크로에 대해 앰퍼샌드 ' & ' 문자를 추가 합니다. 코드에 문자를 다시 추가 하면 안 됩니다.

## <a name="_atl_free_threaded"></a><a name="_atl_free_threaded"></a> _ATL_FREE_THREADED

하나 이상의 개체가 자유 또는 중립 스레딩을 사용 하는지 여부를 정의 합니다.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>설명

자유 스레딩을 지정 합니다. 자유 스레딩은 다중 스레드 아파트 모델과 같습니다. ATL 개체에 사용할 수 있는 스레딩 모델에 대 한 설명은 다른 스레딩 옵션에 대 한 [프로젝트의 스레딩 모델 지정](../../atl/specifying-the-threading-model-for-a-project-atl.md) 및 [옵션, Atl 단순 개체 마법사](../../atl/reference/options-atl-simple-object-wizard.md) 지정을 참조 하세요.

## <a name="_atl_multi_threaded"></a><a name="_atl_multi_threaded"></a> _ATL_MULTI_THREADED

프로젝트에 사용 가능 또는 중립으로 표시 되는 개체를 나타내는 기호입니다.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>설명

이 기호가 정의 된 경우 ATL은 전역 데이터에 대 한 액세스를 올바르게 동기화 하는 코드를 가져옵니다. 새 코드에서는 대신 해당 하는 매크로 [_ATL_FREE_THREADED](#_atl_free_threaded) 를 사용 해야 합니다.

## <a name="_atl_no_automatic_namespace"></a><a name="_atl_no_automatic_namespace"></a> _ATL_NO_AUTOMATIC_NAMESPACE

기본 네임 스페이스를 ATL로 사용할 수 없도록 하는 기호입니다.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>설명

이 기호가 정의 되지 않은 경우 (예를 들어,)는 기본적으로 **네임 스페이스 ATL을 사용 하** 여 수행 되므로 이름 충돌이 발생할 수 있습니다. 이를 방지 하려면이 기호를 정의 합니다.

## <a name="_atl_no_com_support"></a><a name="_atl_no_com_support"></a> _ATL_NO_COM_SUPPORT

COM 관련 코드가 프로젝트를 사용 하 여 컴파일되지 않도록 하는 기호입니다.

```
_ATL_NO_COM_SUPPORT
```

## <a name="atl_no_vtable"></a><a name="atl_no_vtable"></a> ATL_NO_VTABLE

클래스의 생성자와 소멸자에서 vtable 포인터가 초기화 되지 않도록 하는 기호입니다.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>설명

클래스의 생성자와 소멸자에서 vtable 포인터를 초기화할 수 없는 경우 링커에서는 vtable 및 해당 함수가 가리키는 모든 함수를 제거할 수 있습니다. 을로 확장 **`__declspec(novtable)`** 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

## <a name="atl_noinline"></a><a name="atl_noinline"></a> ATL_NOINLINE

함수를 인라인 하지 않아야 함을 나타내는 기호입니다.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>매개 변수

*myfunction*<br/>
인라인되지 말아야 하는 함수입니다.

### <a name="remarks"></a>설명

컴파일러가 헤더 파일에 배치할 수 있도록 인라인으로 선언 되어야 하지만 컴파일러가 인라인 함수를 사용 하지 않도록 하려면이 기호를 사용 합니다. 을로 확장 **`__declspec(noinline)`** 합니다.

## <a name="_atl_single_threaded"></a><a name="_atl_single_threaded"></a> _ATL_SINGLE_THREADED

모든 개체가 단일 스레딩 모델을 사용 하는지 여부를 정의 합니다.

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>설명

개체가 항상 주 COM 스레드에서 실행 되도록 지정 합니다. ATL 개체에 사용할 수 있는 스레딩 모델에 대 한 설명은 다른 스레딩 옵션에 대 한 [프로젝트의 스레딩 모델 지정](../../atl/specifying-the-threading-model-for-a-project-atl.md) 및 [옵션, Atl 단순 개체 마법사](../../atl/reference/options-atl-simple-object-wizard.md) 지정을 참조 하세요.

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)
