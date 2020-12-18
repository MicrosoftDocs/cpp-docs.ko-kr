---
description: '자세한 정보: ASSERT 대신 VERIFY 사용'
title: ASSERT 대신 VERIFY 사용
ms.date: 05/06/2019
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: cbb878e9184536a6888b84f7861a3e8b7b9ab2b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199053"
---
# <a name="using-verify-instead-of-assert"></a>ASSERT 대신 VERIFY 사용

MFC 애플리케이션의 디버그 버전을 실행할 때 문제가 발생하지 않는 것으로 가정합니다. 그러나 동일한 애플리케이션의 릴리스 버전은 충돌하고, 잘못된 결과를 반환하거나, 다른 비정상적인 동작을 보여줍니다.

이 문제는 ASSERT 문에 중요한 코드를 배치하여 올바르게 수행 되는지 확인하는 경우에 발생할 수 있습니다. ASSERT 문은 MFC 프로그램의 릴리스 빌드에서 주석으로 처리되기 때문에 릴리스 빌드에서는 코드가 실행되지 않습니다.

ASSERT를 사용하여 함수 호출이 성공했는지 확인하는 경우 대신에 [확인](../mfc/reference/diagnostic-services.md#verify)을 사용하는 것이 좋습니다. VERIFY 매크로는 애플리케이션의 디버그 및 릴리스 빌드 모두에서 고유한 인수를 평가합니다.

선호되는 또 다른 기법은 함수의 반환 값을 임시 변수에 할당한 다음, ASSERT 문에서 변수를 테스트하는 것입니다.

다음 코드 조각을 살펴보세요.

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

이 코드는 MFC 애플리케이션의 디버그 버전에서 완벽하게 실행됩니다. `calloc( )`에 대한 호출이 실패하면 파일 및 줄 번호를 포함하는 진단 메시지가 표시됩니다. 그러나 MFC 애플리케이션의 정품 빌드에서는

- `calloc( )`에 대한 호출이 발생하지 않아 `buf`가 초기화되지 않은 상태로 유지됩니다. 또는

- `strcpy_s( )`가 "`Hello, World`"를 임의의 메모리 부분으로 복사하여 애플리케이션에 충돌이 발생하거나 시스템의 응답이 중지될 수 있습니다. 또는

- `free()`가 할당된 적이 없는 메모리의 해제를 시도합니다.

ASSERT를 올바르게 사용하려면 코드 샘플을 다음과 같이 변경해야 합니다.

```
enum {
    sizeOfBuffer = 20
};
char *buf;
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );
ASSERT( buf != NULL );
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

또는 다음과 같이 VERIFY를 대신 사용할 수 있습니다.

```
enum {
    sizeOfBuffer = 20
};
char *buf;
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

## <a name="see-also"></a>참조

[릴리스 빌드 문제 해결](fixing-release-build-problems.md)
