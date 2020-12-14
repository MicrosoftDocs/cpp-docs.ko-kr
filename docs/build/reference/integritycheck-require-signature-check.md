---
description: 다음에 대 한 자세한 정보:/INTEGRITYCHECK (서명 확인 필요)
title: /INTEGRITYCHECK(시그니처 확인 필요)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: 650b5d6ae121a5e776f16797a869dfa15f443bf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191266"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK(시그니처 확인 필요)

로드 시 이진 이미지의 디지털 서명을 확인 하도록 지정 합니다.

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>설명

기본적으로 **/Integritycheck** 는 해제 되어 있습니다.

**/Integritycheck** 옵션은 DLL 파일 또는 실행 파일의 PE 헤더에서, Windows에서 이미지를 로드 하기 위해 디지털 서명을 확인 하는 메모리 관리자에 대 한 플래그를 설정 합니다. 이 옵션은 특정 Windows 기능에서 로드 한 커널 모드 코드를 구현 하는 32 비트 및 64 비트 Dll에 대해 설정 해야 하며, Windows Vista, Windows 7, Windows 8, Windows Server 2008 및 Windows Server 2012의 모든 장치 드라이버에 권장 됩니다. Windows Vista 이전의 Windows 버전은이 플래그를 무시 합니다. 자세한 내용은 [pe (이식 가능한 실행 파일) 파일의 강제 무결성 서명](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)을 참조 하세요.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Visual Studio에서 이 링커 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성** 노드를 확장합니다.

1. **링커** 노드를 확장합니다.

1. **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 에서 또는를 `/INTEGRITYCHECK` 입력 `/INTEGRITYCHECK:NO` 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)<br/>
[PE (이식 가능한 실행) 파일의 강제 무결성 서명](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[커널 모드 코드 서명 요구 사항](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)<br/>
[AppInit Dll 및 보안 부팅](/windows/win32/dlls/secure-boot-and-appinit-dlls)
