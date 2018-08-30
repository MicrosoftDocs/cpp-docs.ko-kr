---
title: '방법: PInvoke를 사용 하 여 관리 되는 코드에서 네이티브 Dll 호출 | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9ddd919fb621c971425e9763cf781e5ff0b1c731
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195670"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>방법: PInvoke를 사용하여 관리 코드로부터 네이티브 DLL 호출
플랫폼 호출 (P/Invoke) 기능을 사용 하 여 관리 코드에서 관리 되지 않는 Dll에서 구현 되는 함수를 호출할 수 있습니다. DLL에 대 한 소스 코드를 사용할 수 없는 경우 P/Invoke 상호 운용에 대 한 유일한 옵션입니다. 그러나 다른.NET 언어와 달리 Visual c + + P/Invoke를 대안을 제공합니다. 자세한 내용은 [c + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)합니다.  
  
## <a name="example"></a>예제  
 다음 코드 예제에서는 Win32 [GetSystemMetrics](https://msdn.microsoft.com/library/windows/desktop/ms724385) 현재 픽셀의 화면 해상도 검색 하는 함수입니다.  
  
 내장 형식만 인수로 사용할 값을 반환 하는 함수에 대 한 추가 작업 없이 필요 합니다. 함수 포인터, 배열 및 구조와 같은 다른 데이터 형식에 적절 한 데이터 마샬링이 되도록 추가 특성을 필요 합니다.  
  
 필요한 경우에 것이 좋습니다이 예제에서 설명한 대로 전역 네임 스페이스에 존재 하지 않는 있도록 P/Invoke 선언 값 클래스의 정적 멤버를 확인 합니다.  
  
```  
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
 [C++에서 명시적 PInvoke 사용(DllImport 특성)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)