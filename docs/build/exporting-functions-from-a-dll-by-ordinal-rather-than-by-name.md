---
title: 이름 대신 서수를 사용하여 DLL에서 함수 내보내기
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 66e99b18d181e9067e90398c35a61db2da66c301
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328584"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>이름 대신 서수를 사용하여 DLL에서 함수 내보내기

DLL에서 함수를 내보내는 가장 간단한 방법은 함수를 이름으로 내보내는 것입니다. 예를 들어 **__declspec(dllexport)를**사용할 때 발생합니다. 그러나 대신 서수로 함수를 내보낼 수 있습니다. 이 기술을 사용하면 **__declspec(dllexport)** 대신 .def 파일을 사용해야 합니다. 함수의 서수 값을 지정하려면 .def 파일의 함수 이름에 해당 서수를 부가합니다. 서수 지정에 대한 자세한 내용은 [.def 파일을 사용하여 DLL에서 내보내기를](exporting-from-a-dll-using-def-files.md)참조하십시오.

> [!TIP]
> DLL의 파일 크기를 최적화하려면 내보낸 각 함수에서 **NONAME** 특성을 사용합니다. **NONAME** 특성을 사용하면 서수는 함수 이름이 아닌 DLL의 내보내기 테이블에 저장됩니다. 많은 함수를 내보내는 경우 상당한 절감 효과를 볼 수 있습니다.

## <a name="what-do-you-want-to-do"></a>수행 작업

- [서수로 내보낼 수 있도록 .def 파일을 사용합니다.](exporting-from-a-dll-using-def-files.md)

- [__declspec 사용(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>참고 항목

[DLL에서 내보내기](exporting-from-a-dll.md)
