---
description: '다음에 대 한 자세한 정보: 링크 옵션 Compiler-Controlled'
title: Compiler-Controlled LINK Options
ms.date: 11/04/2016
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: 86f03f53fe19f6788528dca421fb6030289fca99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178981"
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options

/C 옵션을 지정 하지 않으면 CL 컴파일러가 LINK를 자동으로 호출 합니다. CL은 명령줄 옵션 및 인수를 통해 링커에 대 한 일부 제어를 제공 합니다. 다음 표에는 연결에 영향을 주는 CL의 기능이 요약 되어 있습니다.

|CL 사양|링크에 영향을 주는 CL 동작|
|----------------------|---------------------------------|
|.C,. .cxx, .cpp 또는 .def 이외의 모든 파일 이름 확장명|연결에 대 한 입력으로 파일 이름을 전달 합니다.|
|*파일 이름*.def|/DEF:*filename*.def를 전달 합니다.|
|/F *번호*|Pass/STACK:*number*|
|/Fd *파일 이름*|/PDB:*filename* 을 전달 합니다.|
|/Fe *파일 이름*|/OUT:*filename*|
|/Fm *파일 이름*|통과/MAP:*filename*|
|/Gy|패키지 함수 (Comdat)를 만듭니다. 함수 수준 링크를 사용 합니다.|
|/LD|/DLL 전달|
|/LDd|/DLL 전달|
|/link|명령줄의 나머지를 링크로 전달 합니다.|
|/MD 또는/MT|.Obj 파일에 기본 라이브러리 이름을 배치 합니다.|
|/MDd 또는/MTd|는 .obj 파일에 기본 라이브러리 이름을 배치 합니다. 기호를 정의 **_DEBUG**|
|/nologo|/NOLOGO를 전달 합니다.|
|/Zd|/DEBUG 전달|
|/Zi 또는/Z7|/DEBUG 전달|
|/Zl|.Obj 파일에서 기본 라이브러리 이름을 생략 합니다.|

자세한 내용은 [MSVC 컴파일러 옵션](compiler-options.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
