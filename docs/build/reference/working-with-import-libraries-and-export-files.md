---
description: '자세한 정보: 가져오기 라이브러리 및 내보내기 파일 작업'
title: 가져오기 라이브러리 및 내보내기 파일을 사용한 작업
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
ms.openlocfilehash: b6e1664aedf5fa87d269e0ff250e6c52d9d18259
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258800"
---
# <a name="working-with-import-libraries-and-export-files"></a>가져오기 라이브러리 및 내보내기 파일을 사용한 작업

/DEF 옵션과 함께 LIB를 사용 하 여 가져오기 라이브러리 및 내보내기 파일을 만들 수 있습니다. LINK는 내보내기 파일을 사용 하 여 내보내기 (일반적으로 DLL (동적 연결 라이브러리))를 포함 하는 프로그램을 빌드하고 가져오기 라이브러리를 사용 하 여 다른 프로그램의 해당 내보내기에 대 한 참조를 확인 합니다.

임시 단계에서 가져오기 라이브러리를 만드는 경우 .dll을 만들기 전에 .dll을 빌드할 때 동일한 개체 파일 집합을 전달 해야 합니다 .이 파일은 가져오기 라이브러리를 빌드할 때 전달 된 것과 같습니다.

대부분의 경우 LIB를 사용 하 여 가져오기 라이브러리를 만들 필요가 없습니다. 내보내기를 포함 하는 프로그램 (실행 파일 또는 DLL)을 연결 하면 LINK에서 내보내기에 대해 설명 하는 가져오기 라이브러리를 자동으로 만듭니다. 나중에 해당 내보내기를 참조 하는 프로그램을 연결 하는 경우 가져오기 라이브러리를 지정 합니다.

그러나 DLL이 직접 또는 간접적으로 가져온 프로그램으로 내보낼 경우 LIB를 사용 하 여 가져오기 라이브러리 중 하나를 만들어야 합니다. LIB는 가져오기 라이브러리를 만들 때 내보내기 파일도 만듭니다. Dll 중 하나를 연결할 때 내보내기 파일을 사용 해야 합니다.

## <a name="see-also"></a>참고 항목

[LIB 참조](lib-reference.md)
