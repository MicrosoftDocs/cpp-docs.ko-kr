---
description: '자세한 정보: 일반적인 Visual C++ 64비트 마이그레이션 문제'
title: 일반적인 Visual C++ 64비트 마이그레이션 문제
ms.date: 05/06/2019
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
ms.openlocfilehash: 86c4618423353a3a7ac217432ce9dfcb0c19061b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156894"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>일반적인 Visual C++ 64비트 마이그레이션 문제

MSVC(Microsoft C++ 컴파일러)를 사용하여 64비트 Windows 운영 체제에서 실행되는 애플리케이션을 만들 때는 다음 문제를 고려해야 합니다.

- **`int`** 및 **`long`** 은 64비트 Windows 운영 체제에서 32비트 값입니다. 64비트 플랫폼용으로 컴파일하려는 프로그램의 경우 포인터를 32비트 변수에 할당하지 않도록 주의해야 합니다. 포인터는 64비트 플랫폼에서 64비트이며, 이를 32비트 변수에 할당하면 포인터 값이 잘립니다.

- `size_t`, `time_t` 및 `ptrdiff_t`는 64비트 Windows 운영 체제에서 64비트 값입니다.

- Visual Studio 2005 이전 버전에서 `time_t`는 32비트 Windows 운영 체제에 사용되는 32비트 값입니다. `time_t`는 이제 기본적으로 64비트 정수입니다. 자세한 내용은 [시간 관리](../c-runtime-library/time-management.md)를 참조하세요.

   코드의 어느 부분에서 **`int`** 값을 가져와 `size_t` 또는 `time_t` 값으로 처리하는지 알아야 합니다. 숫자가 32비트보다 커져 **`int`** 스토리지로 다시 전달될 때 데이터가 잘릴 수 있습니다.

%x(16진수 **`int`** 형식) `printf` 한정자는 64비트 Windows 운영 체제에서 예상한 대로 작동하지 않습니다. 이 한정자는 전달된 값의 처음 32비트에 대해서만 작동합니다.

- 32비트 Windows 운영 체제에서 정수를 나타내려면 %I32x를 사용합니다.

- 64비트 Windows 운영 체제에서 정수를 나타내려면 %I64x를 사용합니다.

- %p(16진수 포인터 형식)는 64비트 Windows 운영 체제에서 예상한 대로 작동됩니다.

자세한 내용은 다음을 참조하세요.

- [MSVC 컴파일러 옵션](reference/compiler-options.md)

- [마이그레이션 팁](/windows/win32/WinProg64/migration-tips)

## <a name="see-also"></a>참조

[64비트, x64 대상에 대한 C++ 프로젝트 구성](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Visual C++ 포팅 및 업그레이드 가이드](../porting/visual-cpp-porting-and-upgrading-guide.md)
