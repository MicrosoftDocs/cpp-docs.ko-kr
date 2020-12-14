---
description: 자세히 알아보기:/WHOLEARCHIVE (모든 라이브러리 개체 파일 포함)
title: /WHOLEARCHIVE (모든 라이브러리 개체 파일 포함)
ms.date: 02/12/2020
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: 1cbc2ad29bab124af90551d2f4a96ee9f08c578c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259177"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE (모든 라이브러리 개체 파일 포함)

링커가 연결 된 실행 파일의 정적 라이브러리에 모든 개체 파일을 포함 하도록 강제 합니다.

## <a name="syntax"></a>Syntax

> **/WHOLEARCHIVE**\
> **/WHOLEARCHIVE:**_라이브러리_

### <a name="arguments"></a>인수

*라이브러리*\
정적 라이브러리의 선택적 경로 이름입니다. 링커에는이 라이브러리의 모든 개체 파일이 포함 되어 있습니다.

## <a name="remarks"></a>설명

/WHOLEARCHIVE 옵션을 지정 하면 링커에서는 지정 된 정적 라이브러리의 모든 개체 파일 또는 라이브러리를 지정 하지 않은 경우에는 LINK 명령에 지정 된 모든 정적 라이브러리에서 해당 파일을 포함 합니다. 여러 라이브러리에 대해/WHOLEARCHIVE 옵션을 지정 하려면 링커 명령줄에서 둘 이상의/WHOLEARCHIVE 스위치를 사용할 수 있습니다. 기본적으로 링커는 실행 파일의 다른 개체 파일에서 참조 하는 기호를 내보내는 경우에만 연결 된 출력에 개체 파일을 포함 합니다. /WHOLEARCHIVE 옵션을 사용 하면 링커는 정적 라이브러리에 보관 된 모든 개체 파일을 링커 명령줄에 개별적으로 지정 된 것 처럼 처리 합니다.

/WHOLEARCHIVE 옵션을 사용 하 여 정적 라이브러리에서 모든 기호를 다시 내보낼 수 있습니다. 이렇게 하면 둘 이상의 정적 라이브러리에서 구성 요소를 만들 때 모든 라이브러리 코드, 리소스 및 메타 데이터가 포함 되도록 할 수 있습니다. 내보내기에 대 한 Windows 런타임 구성 요소가 포함 된 정적 라이브러리를 만들 때 LNK4264 경고가 표시 되는 경우 다른 구성 요소나 앱에 해당 라이브러리를 연결할 때/WHOLEARCHIVE 옵션을 사용 합니다.

/WHOLEARCHIVE 옵션은 Visual Studio 2015 업데이트 2에서 도입 되었습니다.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Visual Studio에서 이 링커 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**, **링커** 아래에서 **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 텍스트 상자에/WHOLEARCHIVE 옵션을 추가 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
