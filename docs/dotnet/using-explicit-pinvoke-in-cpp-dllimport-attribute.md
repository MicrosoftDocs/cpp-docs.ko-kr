---
description: '자세한 정보: c + +에서 명시적 PInvoke 사용 (DllImport 특성)'
title: C++에서 명시적 PInvoke 사용(DllImport 특성)
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
ms.openlocfilehash: 6c49195cdb677474809435a5bd826808260680e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305479"
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>C++에서 명시적 PInvoke 사용(DllImport 특성)

.NET Framework는 `Dllimport` 관리 되는 응용 프로그램에서 dll 내에 패키지 된 관리 되지 않는 함수를 호출할 수 있도록 하는 특성으로 명시적 플랫폼 호출 (또는 PInvoke) 기능을 제공 합니다. 관리 되지 않는 Api가 Dll로 패키지 되 고 소스 코드를 사용할 수 없는 경우에는 명시적 PInvoke가 필요 합니다. 예를 들어, Win32 함수를 호출 하려면 PInvoke가 필요 합니다. 그렇지 않으면 암시적 P {Invoke를 사용 합니다. 자세한 내용은 [c + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md) 을 참조 하세요.

PInvoke는를 사용 하 여 작동 <xref:System.Runtime.InteropServices.DllImportAttribute> 합니다. DLL의 이름을 첫 번째 인수로 사용 하는이 특성은 사용 되는 각 DLL 진입점에 대 한 함수 선언 앞에 배치 됩니다. 함수의 서명은 DLL에서 내보낸 함수의 이름과 일치 해야 하지만 일부 형식 변환은 `DllImport` 관리 되는 형식 측면에서 선언을 정의 하 여 암시적으로 수행할 수 있습니다.

그 결과는 필요한 전환 코드 (또는 썽크)와 단순 데이터 변환이 포함 된 각 네이티브 DLL 함수에 대 한 관리 되는 진입점입니다. 그런 다음 관리 되는 함수는 이러한 진입점을 통해 DLL을 호출할 수 있습니다. PInvoke의 결과로 모듈에 삽입 된 코드는 완전히 관리 됩니다.

## <a name="in-this-section"></a>섹션 내용

- [관리 코드에서 네이티브 함수 호출](../dotnet/calling-native-functions-from-managed-code.md)

- [방법: PInvoke를 사용 하 여 관리 코드에서 네이티브 Dll 호출](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)

- [방법: PInvoke를 사용 하 여 문자열 마샬링](../dotnet/how-to-marshal-strings-using-pinvoke.md)

- [방법: PInvoke를 사용 하 여 구조체 마샬링](../dotnet/how-to-marshal-structures-using-pinvoke.md)

- [방법: PInvoke를 사용 하 여 배열 마샬링](../dotnet/how-to-marshal-arrays-using-pinvoke.md)

- [방법: PInvoke를 사용 하 여 함수 포인터 마샬링](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)

- [방법: PInvoke를 사용 하 여 포함 포인터 마샬링](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)

## <a name="see-also"></a>참고 항목

[관리 코드에서 네이티브 함수 호출](../dotnet/calling-native-functions-from-managed-code.md)
