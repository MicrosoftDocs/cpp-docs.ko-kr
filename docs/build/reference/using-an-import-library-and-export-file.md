---
title: 가져오기 라이브러리 및 내보내기 파일 사용
ms.date: 11/04/2016
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
ms.openlocfilehash: e23b729bdca102ec24c4426e9784e3aab267bff2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484962"
---
# <a name="using-an-import-library-and-export-file"></a>가져오기 라이브러리 및 내보내기 파일 사용

(실행 파일 또는 DLL)를 가져오기도 수행 하는 다른 프로그램을 내보내는 경우 프로그램 경우 나 두 개 이상의 프로그램 모두를 내보내고 서로, 이러한 프로그램을 링크 하는 명령은 해야 순환 내보내기를 허용 합니다.

순환 내보내기 사용 하지 않는 경우, 다른 응용 프로그램에서 내보내기를 사용 하는 프로그램을 연결 하는 경우 내보내는 프로그램에 대 한 가져오기 라이브러리를 지정 해야 합니다. 내보내는 프로그램에 대 한 가져오기 라이브러리 내보내기는 프로그램을 연결할 때 생성 됩니다. 따라서 내보내는 프로그램을 가져오는 프로그램 먼저 연결 해야 합니다. 예를 들어 TWO.dll ONE.dll에서 가져오면, 먼저 가져오기 라이브러리 ONE.lib 받고 ONE.dll를 연결 합니다. 그런 다음 TWO.dll 링크할 때 ONE.lib 지정 합니다. 링커 TWO.dll를 만들 때 해당 가져오기 라이브러리, TWO.lib도 만듭니다. TWO.lib TWO.dll에서 가져올 있는 프로그램을 링크할 때 사용 합니다.

그러나 순환 내보내기 상황에서는 수 없는 모든 상호 종속적인 다른 프로그램에서 가져오기 라이브러리를 사용 하 여 프로그램을 연결 합니다. TWO.dll ONE.dll도 내보냅니다, TWO.dll에 대 한 가져오기 라이브러리 없습니다 아직 ONE.dll 연결 되는 경우 앞에서 설명한 예제입니다. 순환 내보내기가 있는 경우에 프로그램 중 하나에 대 한 파일 내보내기 및 가져오기 라이브러리를 만드는 LIB를 사용 해야 합니다.

시작 하려면 LIB 실행 하는 프로그램 중 하나를 선택 합니다. LIB 명령에서 모든 개체 및 프로그램에 대 한 라이브러리를 나열 하 고 /def를 지정 프로그램에서 /EXPORT 사양 또는.def 파일을 사용 하는 경우 이러한 항목도 지정 합니다.

가져오기 라이브러리 (.lib) 및 프로그램에 대 한 내보내기 (.exp) 파일을 만든 후 다른 프로그램 또는 프로그램을 연결 하는 경우 가져오기 라이브러리를 사용 합니다. 링크는 빌드하는 각 내보내기 프로그램에 대 한 가져오기 라이브러리를 만듭니다. 예를 들어 ONE.dll 개체 및 내보내기에 LIB를 실행 한 경우 만들고 ONE.lib ONE.exp 합니다. TWO.dll; 링크할 때 ONE.lib를 이제 사용할 수 있습니다. 이 단계는 또한 TWO.lib 가져오기 라이브러리를 만듭니다.

마지막으로 작업을 시작한 프로그램을 연결 합니다. 링크 명령에서 개체 및 프로그램의 경우 프로그램 및 가져오기 라이브러리에 대 한 생성 LIB.exp 파일을 라이브러리 또는 프로그램이 사용 하는 내보내기에 대 한 라이브러리를 지정 합니다. 예제를 계속 하려면 ONE.dll 링크 명령을 ONE.exp TWO.lib, 뿐만 아니라 개체 및 ONE.dll에 포함 된 라이브러리를 포함 합니다. LINK 명령;.def 파일 또는 /EXPORT 사양을 지정 하지 않으면 여기에 필요 하지 내보내기 정의 사용 하는.exp 파일에 포함 되어 있으므로. .Exp 파일을 사용 하 여 연결 하면 링크 가져오기 라이브러리를 만들지 않으므로, 가정 때문에 사용 하는.exp 파일을 만들 때 생성 되었습니다.

## <a name="see-also"></a>참고 항목

[가져오기 라이브러리 및 내보내기 파일을 사용한 작업](../../build/reference/working-with-import-libraries-and-export-files.md)