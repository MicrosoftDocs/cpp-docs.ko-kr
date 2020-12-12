---
description: 자세한 내용은 Module-Definition ()을 (를) 확인 하세요. Def) 파일
title: 모듈 정의(.Def) 파일
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: d52141a2917b2c82616597b2d070a84b96d1a653
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137815"
---
# <a name="module-definition-def-files"></a>모듈 정의(.Def) 파일

모듈 정의 (.def) 파일은 연결 될 프로그램에 대 한 내보내기, 특성 및 기타 정보에 대 한 정보를 링커에 제공 합니다. .Def 파일은 DLL을 빌드할 때 가장 유용 합니다. 모듈 정의 문 대신 사용할 수 있는 [MSVC 링커 옵션이](linker-options.md) 있으므로 .def 파일은 일반적으로 필요 하지 않습니다. 내보낸 함수를 지정 하는 방법으로 [__declspec (dllexport)](../exporting-from-a-dll-using-declspec-dllexport.md) 를 사용할 수도 있습니다.

[/Def (Module-Definition 파일 지정)](def-specify-module-definition-file.md) 링커 옵션을 사용 하 여 링커 단계에서 .def 파일을 호출할 수 있습니다.

내보내기가 없는 .exe 파일을 빌드하는 경우 .def 파일을 사용 하면 출력 파일이 커지고 로드 속도가 느려집니다.

예제는 [DEF 파일을 사용 하 여 DLL에서 내보내기](../exporting-from-a-dll-using-def-files.md)를 참조 하세요.

자세한 내용은 다음 섹션을 참조하십시오.

- [Module-Definition 문에 대 한 규칙](rules-for-module-definition-statements.md)

- [내보내도록](exports.md)

- [HEAPSIZE](heapsize.md)

- [라이브러리](library.md)

- [이름](name-c-cpp.md)

- [섹션이](sections-c-cpp.md)

- [STACKSIZE](stacksize.md)

- [RPC](stub.md)

- [VERSION](version-c-cpp.md)

- [예약어](reserved-words.md)

## <a name="see-also"></a>참조

[C/C++ 빌드 참조](c-cpp-building-reference.md)<br/>
[MSVC 링커 옵션](linker-options.md)
