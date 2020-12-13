---
description: '자세히 알아보기: 창 클래스 매크로'
title: 창 클래스 매크로
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: eb1abcdfea2f3f7e3a8859473d3fabe734906afe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138687"
---
# <a name="window-class-macros"></a>창 클래스 매크로

이러한 매크로는 창 클래스 유틸리티를 정의 합니다.

|Name|설명|
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|새 창 클래스의 이름을 지정할 수 있습니다.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) 새 창 클래스의 이름과 새 클래스에 사용할 창 프로시저를 포함 하는 바깥쪽 클래스의 이름을 지정할 수 있습니다.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|새 창 클래스의 기반이 되는 기존 창 클래스의 이름을 지정할 수 있습니다.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|클래스의 매개 변수를 지정할 수 있습니다.|

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="declare_wnd_class"></a><a name="declare_wnd_class"></a> DECLARE_WND_CLASS

새 창 클래스의 이름을 지정할 수 있습니다. 이 매크로를 ATL ActiveX 컨트롤의 컨트롤 클래스에 놓습니다.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>매개 변수

*WndClassName*<br/>
진행 새 창 클래스의 이름입니다. NULL 인 경우 ATL은 창 클래스 이름을 생성 합니다.

### <a name="remarks"></a>설명

/Permissive-컴파일러 옵션을 사용 하는 경우 DECLARE_WND_CLASS 컴파일러 오류가 발생 합니다. 대신 DECLARE_WND_CLASS2를 사용 해야 합니다.

DECLARE_WND_CLASS를 사용 하 여 [CWndClassInfo](cwndclassinfo-class.md)에서 관리 되는 정보를 포함 하는 새 창 클래스의 이름을 지정할 수 있습니다. DECLARE_WND_CLASS는 다음 정적 함수를 구현 하 여 새 창 클래스를 정의 합니다.

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS 새 창에 대해 다음과 같은 스타일을 지정 합니다.

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

또한 DECLARE_WND_CLASS는 기본 창의 배경색을 지정 합니다. [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) 매크로를 사용 하 여 고유한 스타일과 배경색을 제공 합니다.

[CWindowImpl](cwindowimpl-class.md) 는 DECLARE_WND_CLASS 매크로를 사용 하 여 새 창 클래스를 기반으로 창을 만듭니다. 이 동작을 재정의 하려면 [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) 매크로를 사용 하거나 [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) 함수의 고유한 구현을 제공 합니다.

ATL에서 windows를 사용 하는 방법에 대 한 자세한 내용은 [Atl 창 클래스](../../atl/atl-window-classes.md)문서를 참조 하세요.

## <a name="declare_wnd_class2"></a><a name="declare_wnd_class2"></a> DECLARE_WND_CLASS2

(Visual Studio 2017) DECLARE_WND_CLASS와 유사 하지만/permissive-옵션을 사용 하 여 컴파일할 때 종속 이름 오류를 방지 하는 추가 매개 변수가 있습니다.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>매개 변수

*WndClassName*<br/>
진행 새 창 클래스의 이름입니다. NULL 인 경우 ATL은 창 클래스 이름을 생성 합니다.

*EnclosingClass*<br/>
진행 새 창 클래스를 포함 하는 창 클래스의 이름입니다. NULL이 될 수 없습니다.

### <a name="remarks"></a>설명

/Permissive-옵션을 사용 하는 경우 DECLARE_WND_CLASS에 종속 이름이 포함 되어 있으므로 컴파일 오류가 발생 합니다. DECLARE_WND_CLASS2를 사용 하려면이 매크로를 사용 하는 클래스의 이름을 명시적으로 지정 해야 하며/permissive-플래그에서 오류를 발생 시 키 지 않습니다.
그렇지 않으면이 매크로는 [DECLARE_WND_CLASS](#declare_wnd_class)와 동일 합니다.

## <a name="declare_wnd_superclass"></a><a name="declare_wnd_superclass"></a> DECLARE_WND_SUPERCLASS

클래스의 매개 변수를 지정할 수 있습니다. 이 매크로를 ATL ActiveX 컨트롤의 컨트롤 클래스에 놓습니다.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>매개 변수

*WndClassName*<br/>
진행 슈퍼 클래스에서 *OrigWndClassName* 하는 창 클래스의 이름입니다. NULL 인 경우 ATL은 창 클래스 이름을 생성 합니다.

*OrigWndClassName*<br/>
진행 기존 창 클래스의 이름입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 기존 창 클래스의 슈퍼 클래스를 지정할 창 클래스의 이름을 지정할 수 있습니다. [CWndClassInfo](cwndclassinfo-class.md) 는 슈퍼 클래스의 정보를 관리 합니다.

DECLARE_WND_SUPERCLASS는 다음 정적 함수를 구현 합니다.

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

기본적으로 [CWindowImpl](cwindowimpl-class.md) 는 [DECLARE_WND_CLASS](#declare_wnd_class) 매크로를 사용 하 여 새 창 클래스를 기반으로 창을 만듭니다. 파생 클래스에서 DECLARE_WND_SUPERCLASS 매크로를 지정 하 여 `CWindowImpl` window 클래스는 기존 클래스를 기반으로 하지만 창 프로시저를 사용 합니다. 이 기법은 superclassing 라고 합니다.

DECLARE_WND_CLASS 및 DECLARE_WND_SUPERCLASS 매크로를 사용 하는 것 외에도 [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) 함수를 고유한 구현으로 재정의할 수 있습니다.

ATL에서 windows를 사용 하는 방법에 대 한 자세한 내용은 [Atl 창 클래스](../../atl/atl-window-classes.md)문서를 참조 하세요.

## <a name="declare_wnd_class_ex"></a><a name="declare_wnd_class_ex"></a> DECLARE_WND_CLASS_EX

새 창 클래스의 기반이 되는 기존 창 클래스의 이름을 지정할 수 있습니다. 이 매크로를 ATL ActiveX 컨트롤의 컨트롤 클래스에 놓습니다.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>매개 변수

*WndClassName*<br/>
진행 새 창 클래스의 이름입니다. NULL 인 경우 ATL은 창 클래스 이름을 생성 합니다.

*style*<br/>
진행 창의 스타일입니다.

*배경*<br/>
진행 창의 배경색입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 [CWndClassInfo](cwndclassinfo-class.md)에서 관리 되는 정보를 포함 하는 새 창 클래스의 클래스 매개 변수를 지정할 수 있습니다. DECLARE_WND_CLASS_EX는 다음 정적 함수를 구현 하 여 새 창 클래스를 정의 합니다.

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

기본 스타일 및 배경색을 사용 하려면 [DECLARE_WND_CLASS](#declare_wnd_class) 매크로를 사용 합니다. ATL에서 windows를 사용 하는 방법에 대 한 자세한 내용은 [Atl 창 클래스](../../atl/atl-window-classes.md)문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[매크로](atl-macros.md)
