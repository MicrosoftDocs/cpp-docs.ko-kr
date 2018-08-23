---
title: 심각한 오류 C1905 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1905
dev_langs:
- C++
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 608702deb1ebaed9bab56fe8d08ca3102d5c5d89
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541679"
---
# <a name="fatal-error-c1905"></a>심각한 오류 C1905
프런트 엔드와 백 엔드가 호환되지 않습니다. 같은 프로세서를 대상으로 해야 합니다.  
  
 이 오류는.obj 파일 컴파일러 프런트 엔드 (c1.dll) 프로세서를 대상에 같은 x86, ARM, x64에서 생성 되지만 다른 프로세서를 대상으로 하는 백 엔드 (c2.dll)에서 읽을 때 발생 합니다.  
  
 이 문제를 해결하려면 사용 중인 프런트 엔드와 백 엔드가 일치하는지 확인합니다. Visual Studio에서 만든 프로젝트의 경우 기본적으로 일치하는 프런트 엔드와 백 엔드가 사용됩니다. 컴파일러 도구에 대해 다른 경로를 사용하도록 프로젝트 파일을 편집한 경우 이 오류가 발생할 수 있습니다. 컴파일러 도구의 경로를 구체적으로 설정하지 않은 경우 설치한 Visual Studio가 손상되면 이 오류가 발생할 수 있습니다. 컴파일러 .dll 파일을 한 위치에서 다른 위치로 복사한 경우를 예로 들 수 있습니다. 사용 하 여 **프로그램 및 기능** 을 복구 하거나 Visual Studio를 다시 설치 하려면 Windows 제어판에서.