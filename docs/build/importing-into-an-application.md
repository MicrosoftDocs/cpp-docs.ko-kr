---
description: '자세한 정보: 애플리케이션으로 가져오기'
title: 애플리케이션으로 가져오기
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], importing
- importing DLLs [C++], applications
- applications [C++], importing into
ms.assetid: 9d646466-e12e-4710-8ad9-c819c0375fcc
ms.openlocfilehash: e82f16d9a82f196ff3bb59cc6a7c165d71395a65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162536"
---
# <a name="importing-into-an-application"></a>애플리케이션으로 가져오기

다음 두 가지 방법을 사용하여 함수를 애플리케이션으로 가져올 수 있습니다.

- 주 애플리케이션의 함수 정의에서 **`__declspec(dllimport)`** 키워드 사용

- 모듈 정의(.def) 파일을 **`__declspec(dllimport)`** 과 함께 사용

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [__declspec(dllimport)을 사용하여 애플리케이션으로 가져오기](importing-into-an-application-using-declspec-dllimport.md)

- [__declspec(dllimport)을 사용하여 함수 호출 가져오기](importing-function-calls-using-declspec-dllimport.md)

- [__declspec(dllimport)을 사용하여 데이터 가져오기](importing-data-using-declspec-dllimport.md)

- [DEF 파일을 사용하여 가져오기](importing-using-def-files.md)

## <a name="see-also"></a>참조

[가져오기 및 내보내기](importing-and-exporting.md)
