---
description: '자세한 정보: ATL 프로젝트에 대 한 컴파일러 최적화 지정'
title: ATL 프로젝트에 대해 컴파일러 최적화 지정
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
ms.openlocfilehash: d0650cfebdeb74caeb78a0ab4f138f4896865fc8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138803"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>ATL 프로젝트에 대해 컴파일러 최적화 지정

기본적으로 [ATL 컨트롤 마법사](../../atl/reference/atl-control-wizard.md) 는 다음과 같이 ATL_NO_VTABLE 매크로를 사용 하 여 새 클래스를 생성 합니다.

```
class ATL_NO_VTABLE CProjName
{
...
};
```

그러면 ATL에서 다음과 같이 _ATL_NO_VTABLE를 정의 합니다.

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

_ATL_DISABLE_NO_VTABLE 정의 하지 않으면 ATL_NO_VTABLE 매크로가로 확장 `declspec(novtable)` 됩니다. `declspec(novtable)`클래스 선언에서를 사용 하면 클래스 생성자 및 소멸자에서 vtable 포인터가 초기화 되지 않습니다. 프로젝트를 빌드하면 링커가 가리키는 vtable 및 모든 함수를 제거 합니다.

ATL_NO_VTABLE를 사용 해야 하며, 그 결과 `declspec(novtable)` , 직접 만들 수 없는 기본 클래스만 사용 해야 합니다. 프로젝트 `declspec(novtable)` 에서를 가장 많이 파생 된 클래스와 함께 사용 하면 안 됩니다 .이 클래스 (일반적으로 [CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md)또는 [ccompolyobject](../../atl/reference/ccompolyobject-class.md))는 프로젝트에 대 한 vtable 포인터를 초기화 하기 때문입니다.

에서 사용 하는 개체의 생성자에서 가상 함수를 호출 하면 안 `declspec(novtable)` 됩니다. 이러한 호출 [을 해당 호출을 이전 메서드로 이동](ccomobjectrootex-class.md#finalconstruct) 해야 합니다.

한정자를 사용 해야 하는지 확실 하지 않은 경우 `declspec(novtable)` 클래스 정의에서 ATL_NO_VTABLE 매크로를 제거 하거나를 지정 하 여 전역으로 사용 하지 않도록 설정할 수 있습니다.

```
#define _ATL_DISABLE_NO_VTABLE
```

다른 모든 ATL 헤더 파일이 포함 되기 전에 *.pch. h* (Visual Studio 2017이 하 버전의 *stdafx.h* )에서

## <a name="see-also"></a>참고 항목

[ATL 프로젝트 마법사](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio의 C++ 프로젝트 형식](../../build/reference/visual-cpp-project-types.md)<br/>
[ATL 및 C Run-Time 코드를 사용한 프로그래밍](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 개체의 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[기본 ATL 프로젝트 구성](../../atl/reference/default-atl-project-configurations.md)
