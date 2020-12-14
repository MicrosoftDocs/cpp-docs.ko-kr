---
description: '자세한 정보: 방법: PInvoke를 사용 하 여 관리 코드에서 네이티브 Dll 호출'
title: '방법: PInvoke를 사용하여 관리 코드로부터 네이티브 DLL 호출'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
ms.openlocfilehash: 915601aa813f1c5c14977c1492d6c675125c47be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335396"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>방법: PInvoke를 사용하여 관리 코드로부터 네이티브 DLL 호출

관리 되지 않는 Dll에서 구현 되는 함수는 플랫폼 호출 (P/Invoke) 기능을 사용 하 여 관리 코드에서 호출할 수 있습니다. DLL에 대 한 소스 코드를 사용할 수 없는 경우에는 P/Invoke가 상호 운용을 위한 유일한 옵션입니다. 그러나 다른 .NET 언어와 달리 Visual C++ P/Invoke에 대 한 대안을 제공 합니다. 자세한 내용은 [c + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)을 참조 하세요.

## <a name="example"></a>예제

다음 코드 예제에서는 Win32 [Getsystemmetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) 함수를 사용 하 여 화면의 현재 해상도 (픽셀)를 검색 합니다.

인수 및 반환 값으로 내장 형식만 사용 하는 함수의 경우 추가 작업이 필요 하지 않습니다. 함수 포인터, 배열 및 구조와 같은 기타 데이터 형식에는 적절 한 데이터 마샬링을 보장 하기 위해 추가 특성이 필요 합니다.

반드시 필요한 것은 아니지만,이 예제에서 보여 주는 것 처럼 전역 네임 스페이스에 존재 하지 않도록 P/Invoke 선언에 값 클래스의 정적 멤버를 설정 하는 것이 좋습니다.

```cpp
// pinvoke_basic.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value class Win32 {
public:
   [DllImport("User32.dll")]
   static int GetSystemMetrics(int);

   enum class SystemMetricIndex {
      // Same values as those defined in winuser.h.
      SM_CXSCREEN = 0,
      SM_CYSCREEN = 1
   };
};

int main() {
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);
}
```

## <a name="see-also"></a>참고 항목

[C + +에서 명시적 PInvoke 사용 (DllImport 특성)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
