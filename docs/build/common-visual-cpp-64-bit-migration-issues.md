---
title: 일반적인 Visual C++ 64 비트 마이그레이션 문제
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
ms.openlocfilehash: 004fe7ace6102feecbcb2f542b5b93268ae2f868
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493322"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>일반적인 Visual C++ 64 비트 마이그레이션 문제

Microsoft C++ 컴파일러(MSVC)를 사용하여 64 비트 Windows 운영 체제에서 실행되는 응용 프로그램을 만들 경우 다음 문제에 유의하세요.

- `int`와 `long`은 64비트 Windows 운영 체제 상에서 32비트 값입니다. 프로그램을 64비트 플랫폼용으로 컴파일하려는 계획이 있다면 포인터를 32비트 변수에 할당하지 않도록 주의해야 합니다. 64비트 플랫폼에서 포인터는 64비트이며, 이를 32비트 변수에 할당하면 포인터 값이 잘립니다.

- `size_t`, `time_t` 및 `ptrdiff_t`는 64 비트 Windows 운영 체제 상에서 64 비트 값입니다.

- `time_t`는 Visual Studio 2005 및 이전 버전 32 비트 Windows 운영 체제에서는 32 비트 값입니다. `time_t`는 이제 기본적으로 64 비트 정수입니다. 자세한 내용은 [시간 관리](../c-runtime-library/time-management.md)를 참조합니다.

   코드의 어느 부분에서 `int` 값을 가져와 `size_t` 또는 `time_t` 값으로 처리하는지 알아야 합니다. 숫자가 32비트보다 커져 `int` 스토리지로 다시 전달될 때 데이터가 잘릴 수 있습니다.

%x(16진수 `int` 형식) `printf` 한정자는 64비트 Windows 운영 체제에서 제대로 작동하지 않습니다. 이 한정자는 전달된 값의 앞부분 32비트에 대해서만 작동합니다.

- 32비트 Windows 운영 체제에서 정수를 나타내려면 %I32x를 사용합니다.

- 64비트 Windows 운영 체제에서 정수를 나타내려면 %I64x를 사용합니다.

- %p(16진수 포인터 형식)는 64비트 Windows 운영 체제에서 제대로 작동합니다.

자세한 내용은 다음을 참조하세요.

- [MSVC 컴파일러 옵션](reference/compiler-options.md)

- [마이그레이션 팁](/windows/win32/WinProg64/migration-tips)

## <a name="see-also"></a>참고자료

[64비트, x64를 대상으로 하는 C++ 프로젝트 구성](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Visual C++ 포팅 및 업그레이드 가이드](../porting/visual-cpp-porting-and-upgrading-guide.md)
