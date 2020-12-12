---
description: '자세한 정보: 가져오기 라이브러리 빌드 및 파일 내보내기'
title: 가져오기 라이브러리 및 내보내기 파일 빌드
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
ms.openlocfilehash: 8fbd06ce06d77721e64294b88632933b3ad71a03
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179514"
---
# <a name="building-an-import-library-and-export-file"></a>가져오기 라이브러리 및 내보내기 파일 빌드

가져오기 라이브러리 및 내보내기 파일을 작성 하려면 다음 구문을 사용 합니다.

> **LIB/def**[**:**<em>deffile</em>] [*options*] [*objfiles*] [*라이브러리*]

/DEF를 지정 하면 lib는 LIB 명령으로 전달 되는 내보내기 사양에서 출력 파일을 만듭니다. 내보내기를 지정 하는 방법에는 다음과 같은 세 가지가 있습니다. 권장 되는 사용 순서 대로 나열 됩니다.

1. **`__declspec(dllexport)`** *Objfiles* 또는 *라이브러리* 중 하나의 정의

1. LIB 명령줄에서/EXPORT:*name* 의 사양입니다.

1. *Deffile* 의 **EXPORTS** 문에 있는 정의

이러한 방법은 내보내기 프로그램을 연결할 때 내보내기를 지정 하는 데 사용 하는 방법과 동일 합니다. 프로그램은 둘 이상의 메서드를 사용할 수 있습니다. LINK 명령에서와 마찬가지로 lib 명령의 명령 파일에 LIB 명령의 일부 (예: 여러 *objfiles* 또는/export 사양)를 지정할 수 있습니다.

가져오기 라이브러리 및 내보내기 파일을 빌드하는 데 다음 옵션이 적용 됩니다.

> **/Out:** *가져오기*

만들려는 *가져오기* 라이브러리의 기본 출력 파일 이름을 재정의 합니다. /OUT을 지정 하지 않으면 기본 이름은 LIB 명령의 첫 번째 개체 파일 또는 라이브러리의 기본 이름이 고 확장명은 lib입니다. 내보내기 파일에는 가져오기 라이브러리와 동일한 기본 이름과 .exp 확장명이 지정 됩니다.

> **/Export:** *entryname* \[ **=** *internalname*] \[ , **\@** <em>서 수</em> \[ , **NONAME**]] \[ , **데이터**]

프로그램에서 함수를 내보내 다른 프로그램에서 함수를 호출할 수 있도록 합니다. **데이터 키워드를** 사용 하 여 데이터를 내보낼 수도 있습니다. 내보내기는 일반적으로 DLL에 정의 됩니다.

*Entryname* 은 호출 프로그램에서 사용할 함수 또는 데이터 항목의 이름입니다. 필요에 따라 *internalname* 를 정의 프로그램에서 알려진 함수로 지정할 수 있습니다. 기본적으로 *internalname* 는 *entryname* 와 동일 합니다. *서 수* 는 1에서 65535 사이의 내보내기 테이블에 인덱스를 지정 합니다. *서 수* 를 지정 하지 않으면 LIB에서 하나를 할당 합니다. **NONAME** 키워드는 *entryname* 없이 서 수로만 함수를 내보냅니다. Data **키워드는** 데이터 전용 개체를 내보내는 데 사용 됩니다.

> **/INCLUDE:** *기호*

지정 된 *기호* 를 기호 테이블에 추가 합니다. 이 옵션은 포함 되지 않는 라이브러리 개체를 강제로 사용 하는 데 유용 합니다.

임시 단계에서 가져오기 라이브러리를 만드는 경우 .dll을 만들기 전에 .dll을 빌드할 때 동일한 개체 파일 집합을 전달 해야 합니다 .이 파일은 가져오기 라이브러리를 빌드할 때 전달 된 것과 같습니다.

## <a name="see-also"></a>참고 항목

[가져오기 라이브러리 및 내보내기 파일을 사용한 작업](working-with-import-libraries-and-export-files.md)
