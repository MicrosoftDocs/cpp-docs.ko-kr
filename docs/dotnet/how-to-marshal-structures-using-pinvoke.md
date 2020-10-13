---
title: '방법: PInvoke를 사용하여 구조체 마샬링'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
ms.openlocfilehash: e132505ef536a79c67afdd76443c2637c08f923b
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008754"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>방법: PInvoke를 사용하여 구조체 마샬링

이 문서에서는 P/Invoke를 사용 하 여 관리 되는 함수에서 C 스타일 구조체를 허용 하는 네이티브 함수를 호출할 수 있는 방법에 대해 설명 합니다. P/Invoke는 컴파일 시간 오류 보고를 거의 제공 하지 않고 c + + Interop 기능을 사용 하는 것이 좋지만, 형식이 안전 하지 않으며, 구현 하기 번거로울 수 있습니다. 관리 되지 않는 API가 DLL로 패키지 되 고 소스 코드를 사용할 수 없는 경우 P/Invoke는 유일한 옵션입니다. 그렇지 않으면 다음 문서를 참조 하세요.

- [C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [방법: PInvoke를 사용 하 여 문자열 마샬링](../dotnet/how-to-marshal-strings-using-pinvoke.md)

기본적으로 네이티브 및 관리 되는 구조체는 메모리에서 다르게 배치 되므로 관리 되는/관리 되지 않는 경계에서 구조를 성공적으로 전달 하려면 데이터 무결성을 유지 하기 위한 추가 단계가 필요 합니다.

이 문서에서는 네이티브 구조체의 관리 되는 항목을 정의 하는 데 필요한 단계 및 결과 구조를 관리 되지 않는 함수로 전달할 수 있는 방법에 대해 설명 합니다. 이 문서에서는 단순 구조 (문자열 또는 포인터를 포함 하지 않는 구조)가 사용 된다고 가정 합니다. 비 blittable 상호 운용성에 대 한 자세한 내용은 [c + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)을 참조 하세요. P/Invoke는 비 blittable 형식을 반환 값으로 사용할 수 없습니다. Blittable 형식에는 관리 코드와 비관리 코드의 동일한 표현이 있습니다. 자세한 내용은 [Blittable 형식 및 비 Blittable 형식](/dotnet/framework/interop/blittable-and-non-blittable-types)을 참조 하세요.

관리 되는/관리 되지 않는 경계에서 단순 하 고 blittable 구조체를 마샬링하면 먼저 각 네이티브 구조체의 관리 되는 버전을 정의 해야 합니다. 이러한 구조는 모든 올바른 이름을 가질 수 있습니다. 데이터 레이아웃이 아닌 두 구조체의 네이티브 버전과 관리 되는 버전 간에는 관계가 없습니다. 따라서 관리 되는 버전에는 기본 버전과 동일한 크기의 필드를 포함 하는 것이 중요 합니다. 구조체의 관리 되는 버전과 네이티브 버전이 동일한 지 확인 하기 위한 메커니즘은 없으므로 런타임에는 비 호환성이 명확 하지 않게 됩니다. 프로그래머는 두 구조체의 데이터 레이아웃이 동일 해야 합니다.

관리 되는 구조체의 멤버는 성능을 위해 다시 정렬 되는 경우가 있기 때문에 특성을 사용 하 여 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 구조가 순차적으로 배치 되도록 해야 합니다. 또한 구조체 압축 설정을 네이티브 구조에서 사용 하는 것과 동일 하 게 설정 하는 것이 좋습니다. 기본적으로 Visual C++는 관리 코드에 대해 8 바이트 구조체 압축을 사용 합니다.

1. 그런 다음를 사용 <xref:System.Runtime.InteropServices.DllImportAttribute> 하 여 구조체를 수락 하는 관리 되지 않는 함수에 해당 하는 진입점을 선언 하지만, 구조체의 두 버전에 동일한 이름을 사용 하는 경우 불과할 지점인 함수 시그니처에서 관리 되는 버전의 구조체를 사용 합니다.

1. 이제 관리 코드는 관리 되는 버전의 구조체를 관리 되지 않는 함수에 실제로 관리 되는 함수로 전달할 수 있습니다. 이러한 구조체는 다음 예제에서 보여 주는 것 처럼 값 또는 참조로 전달 될 수 있습니다.

## <a name="unmanaged-and-a-managed-modules"></a>관리 되지 않는 모듈 및 관리 되는 모듈

다음 코드는 관리 되지 않는 및 관리 모듈로 구성 됩니다. 관리 되지 않는 모듈은 location 구조체의 두 인스턴스를 허용 하는 GetDistance 라는 함수와 Location 이라는 구조체를 정의 하는 DLL입니다. 두 번째 모듈은 GetDistance 함수를 가져오는 관리 되는 명령줄 응용 프로그램 이지만, 위치 구조, MLocation의 관리 되는 항목을 기준으로 정의 합니다. 실제로 동일한 이름을 구조체의 두 버전 모두에 사용할 수 있습니다. 그러나 여기에서 다른 이름을 사용 하 여 DllImport 프로토타입이 관리 되는 버전 측면에서 정의 되었음을 보여 줍니다.

기존 #include 지시어를 사용 하 여 관리 코드에 노출 되는 DLL 부분은 없습니다. 실제로 DLL은 런타임에만 액세스 되므로 DllImport를 사용 하 여 가져온 함수와 관련 된 문제는 컴파일 타임에 검색 되지 않습니다.

### <a name="example-unmanaged-dll-module"></a>예: 관리 되지 않는 DLL 모듈

```cpp
// TraditionalDll3.cpp
// compile with: /LD /EHsc
#include <iostream>
#include <stdio.h>
#include <math.h>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
   #define TRADITIONALDLL_API __declspec(dllexport)
#else
   #define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct Location {
   int x;
   int y;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API double GetDistance(Location, Location);
   TRADITIONALDLL_API void InitLocation(Location*);
}

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}
```

### <a name="example-managed-command-line-application-module"></a>예: 관리 되는 명령줄 응용 프로그램 모듈

```cpp
// MarshalStruct_pi.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MLocation {
   int x;
   int y;
};

value struct TraditionalDLL {
   [DllImport("TraditionalDLL3.dll")]
   static public double GetDistance(MLocation, MLocation);
   [DllImport("TraditionalDLL3.dll")]
   static public double InitLocation(MLocation*);
};

int main() {
   MLocation loc1;
   loc1.x = 0;
   loc1.y = 0;

   MLocation loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = TraditionalDLL::GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   MLocation loc3;
   TraditionalDLL::InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

```Output
[unmanaged] loc1(0,0) loc2(100,100)
[managed] distance = 141.42135623731
[unmanaged] Initializing location...
[managed] x=50 y=50
```

## <a name="see-also"></a>참조

[C + +에서 명시적 PInvoke 사용 (DllImport 특성)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
