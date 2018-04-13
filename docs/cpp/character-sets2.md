---
title: "Sets2 문자 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db505809c1fbc2c49e116b9c2f850f6e14dfbdf6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="character-sets"></a>문자 집합
C++ 프로그램의 텍스트는 특정 문자 인코딩을 사용하는 소스 파일에 저장됩니다. C++ 표준에서는 소스 파일에 대해 기본 소스 문자 집합을 지정하고 컴파일된 파일에 대해 기본 실행 문자 집합을 지정합니다. Visual C++에서는 추가 로캘별 문자 집합을 소스 파일 및 컴파일된 파일에서 사용할 수 있습니다.  
  
## <a name="character-sets"></a>문자 집합  
 C++ 표준에서는 소스 파일에서 사용할 수 있는 *기본 소스 문자 집합* 을 지정합니다. 이 집합 외부에 문자를 나타내려면 *유니버설 문자 이름*을 사용하여 추가 문자를 지정할 수 있습니다. 컴파일된 경우 *기본 실행 문자 집합* 및 *기본 실행 와이드 문자 집합* 은 프로그램에 나타낼 수 있는 문자 및 문자열을 나타냅니다. Visual C++ 구현에서는 소스 코드 및 컴파일된 코드에서 추가 문자를 허용합니다.  
  
### <a name="basic-source-character-set"></a>기본 소스 문자 집합  
 *기본 소스 문자 집합* 은 소스 파일에서 사용할 수 있는 96개 문자로 구성됩니다. 이 집합에는 공백 문자, 가로 탭, 세로 탭, 폼 피드 및 줄 바꿈 제어 문자가 포함되며 다음 그래픽 문자 집합도 포함됩니다.  
  
 `a b c d e f g h i j k l m n o p q r s t u v w x y z`  
  
 `A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`  
  
 `0 1 2 3 4 5 6 7 8 9`  
  
 `_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`  
  
 **Microsoft 전용**  
  
 Visual C++에서는 `$` 문자를 기본 소스 문자 집합의 멤버로 포함합니다. 또한 Visual C++에서는 파일 인코딩에 따라 추가 문자 집합을 소스 파일에서 사용할 수 있습니다. 기본적으로 Visual Studio는 기본 코드 페이지를 사용하여 소스 파일을 저장합니다. 소스 파일이 로캘별 코드 페이지나 유니코드 코드 페이지를 사용하여 저장되는 경우 Visual C++ 에서는 기본 소스 문자 집합에서 명시적으로 허용되지 않는 제어 코드를 제외하고 해당 코드 페이지의 모든 문자를 소스 코드에서 사용할 수 있습니다. 예를 들어 일본어 코드 페이지를 사용하여 파일을 저장하는 경우 주석, 식별자 또는 문자열 리터럴에 일본어 문자를 배치할 수 있습니다. Visual C++에서는 유효한 멀티바이트 문자나 유니코드 코드 포인트로 변환할 수 없는 문자 시퀀스를 허용하지 않습니다. 컴파일러 옵션에 따라 허용되는 일부 문자가 식별자에 나타나지 않을 수 있습니다. 자세한 내용은 [Identifiers](../cpp/identifiers-cpp.md)를 참조하세요.  
  
 **Microsoft 전용 종료**  
  
### <a name="universal-character-names"></a>유니버설 문자 이름  
 C++ 프로그램에서는 기본 소스 문자 집합에 지정된 것보다 훨씬 더 많은 문자를 사용할 수 있으므로 *유니버설 문자 이름*을 사용하여 이식 가능한 방법으로 이러한 문자를 지정할 수 있습니다. 유니버설 문자 이름은 유니코드 코드 포인트를 나타내는 문자 시퀀스로 구성되며,  두 가지 형식을 사용합니다. `\UNNNNNNNN` 을 사용하여 U+NNNNNNNN 형식의 유니코드 코드 포인터를 나타냅니다. 여기서 NNNNNNNN은 8자리 16진수 코드 포인트 번호입니다. 4자리 `\uNNNN` 을 사용하여 U+0000NNNN 형식의 유니코드 코드 포인트를 나타냅니다.  
  
 유니버설 문자 이름은 문자열 및 문자 리터럴과 식별자에서 사용할 수 있습니다. 유니버설 문자 이름은 0xD800-0xDFFF 범위에 있는 서로게이트 코드 포인트를 나타내는 데 사용할 수 없습니다. 대신 원하는 코드 포인트를 사용하면 컴파일러에서 필요한 서로게이트를 자동으로 생성합니다. 식별자에 사용할 수 있는 유니버설 문자 이름에는 추가 제한이 적용됩니다. 자세한 내용은 [Identifiers](../cpp/identifiers-cpp.md) 및 [String and Character Literals](../cpp/string-and-character-literals-cpp.md)을 참조하세요.  
  
 **Microsoft 전용**  
  
 Visual C++ 컴파일러는 유니버설 문자 이름 형식과 리터럴 형식의 문자를 같은 의미로 처리합니다. 예를 들어 유니버설 문자 이름 형식을 사용하여 식별자를 선언하고 리터럴 형식에서 사용할 수 있습니다.  
  
```cpp  
auto \u30AD = 42; // \u30AD is 'キ'  
if (キ == 42) return true; // \u30AD and キ are the same to the compiler  
  
```  
  
 Windows 클립보드의 확장된 문자 형식은 응용 프로그램 로캘 설정과 관련이 있습니다. 다른 응용 프로그램에서 이러한 문자를 잘라내어 코드에 붙여 넣으면 예기치 않은 문자 인코딩이 발생할 수 있습니다. 그러면 표시되는 원인 없이 코드에서 구문 분석 오류가 발생할 수 있습니다. 따라서 확장된 문자를 붙여 넣기 전에 소스 파일 인코딩을 유니코드 코드 페이지로 설정하는 것이 좋습니다. 또한 IME 또는 문자표 앱을 사용하여 확장된 문자를 생성하는 것이 좋습니다.  
  
 **Microsoft 전용 종료**  
  
### <a name="basic-execution-character-set"></a>기본 실행 문자 집합  
 *기본 실행 문자 집합* 및 *기본 실행 와이드 문자 집합* 은 기본 소스 문자 집합의 모든 문자와 경고, 백스페이스, 캐리지 리턴 및 null 문자를 나타내는 제어 문자로 구성됩니다.   *실행 문자 집합* 및 *실행 와이드 문자 집합* 은 기본 집합의 상위 집합입니다. 여기에는 기본 소스 문자 집합 이외에 구현 시 정의된 소스 문자가 포함됩니다. 실행 문자 집합에는 로캘별 표현이 있습니다.