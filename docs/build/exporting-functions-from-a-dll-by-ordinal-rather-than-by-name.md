---
description: '자세한 정보: 이름 대신 서수를 사용하여 DLL에서 함수 내보내기'
title: 이름 대신 서수를 사용하여 DLL에서 함수 내보내기
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 84d200e2c37161d6bef3e64e72130204640088c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156504"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>이름 대신 서수를 사용하여 DLL에서 함수 내보내기

DLL에서 함수를 내보내는 가장 간단한 방법은 이름으로 내보내는 것입니다. 예를 들어 **`__declspec(dllexport)`** 을 사용하는 경우 이 문제가 발생합니다. 그러나 대신 서수로 함수를 내보낼 수 있습니다. 이 기법에서는 **`__declspec(dllexport)`** 대신 .def 파일을 사용해야 합니다. 함수의 서수 값을 지정하려면 .def 파일의 함수 이름에 서수를 추가합니다. 서수 지정에 대한 자세한 내용은 [.def 파일을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-def-files.md)를 참조하세요.

> [!TIP]
> DLL의 파일 크기를 최적화하려면 내보낸 각 함수에서 **NONAME** 특성을 사용합니다. **NONAME** 특성을 사용하면 서수는 함수 이름이 아니라 DLL의 내보내기 테이블에 저장됩니다. 이렇게 하면 많은 함수를 내보내는 경우 상당한 비용을 절감할 수 있습니다.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [서수로 내보낼 수 있도록 .def 파일 사용](exporting-from-a-dll-using-def-files.md)

- [__declspec(dllexport) 사용](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>참조

[DLL에서 내보내기](exporting-from-a-dll.md)
