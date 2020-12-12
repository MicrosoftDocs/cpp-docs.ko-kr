---
description: '자세한 정보: 프로젝트 빌드 오류 PRJ0003'
title: 프로젝트 빌드 오류 PRJ0003
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: cefd56e1d11da77f288333fb0e1f9c10ef684d12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119410"
---
# <a name="project-build-error-prj0003"></a>프로젝트 빌드 오류 PRJ0003

> '*명령줄*'을 생성 하는 동안 오류가 발생 했습니다.

**속성 페이지** 대화 상자의 입력에서 만든 *명령줄* 명령이 오류 코드를 반환 했지만 **출력** 창에 정보가 표시 되지 않습니다.

이 오류가 발생 하는 원인은 다음과 같습니다.

- 프로젝트는 ATL 서버에 종속 됩니다. Visual Studio 2008부터 ATL 서버는 더 이상 Visual Studio의 일부로 포함 되지 않지만 CodePlex에서 공유 원본 프로젝트로 릴리스 되었습니다. ATL 서버 소스 코드 및 도구를 다운로드 하려면 [Atl 서버 라이브러리 및 도구](https://go.microsoft.com/fwlink/p/?linkid=81979)로 이동 합니다.

- 시스템 리소스가 부족 합니다. 이 문제를 해결 하려면 일부 응용 프로그램을 닫으십시오.

- 보안 권한이 부족 합니다. 보안 권한이 충분 한지 확인 합니다.

- **VC + + 디렉터리** 에 지정 된 실행 파일 경로에는 실행 하려는 도구의 경로가 포함 되지 않습니다. 자세한 내용은 [컴파일러 및 빌드 속성 설정](../../build/working-with-project-properties.md) 을 참조 하세요.

- 메이크파일 프로젝트의 경우 **빌드 명령줄** 또는 **다시 작성** 명령줄에서 실행할 명령이 없습니다.

## <a name="see-also"></a>참고 항목

[프로젝트 빌드 오류 및 경고 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
