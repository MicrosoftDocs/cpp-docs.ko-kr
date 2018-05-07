---
title: '방법: 정규식을 사용 하 여 문자열 구문 분석 (C + + /cli CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- strings [C++], parsing
ms.assetid: 5b0c7ca3-9bba-4389-a45c-6d373cff91b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5940a59d7e9b4e68f289848523710594621e73d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-parse-strings-using-regular-expressions-ccli"></a>방법: 정규식을 사용하여 문자열 구문 분석(C++/CLI)
다음 코드 예제에서는 간단한 문자열을 사용 하 여 구문 분석 하는 방법을 보여 줍니다는 <xref:System.Text.RegularExpressions.Regex> 클래스에 <xref:System.Text.RegularExpressions?displayProperty=fullName> 네임 스페이스입니다. 여러 유형의 단어 설명자를 포함 하는 문자열을 생성 합니다. 문자열 구문 분석 사용 하 여 <xref:System.Text.RegularExpressions.Regex> 클래스와 함께 <xref:System.Text.RegularExpressions.Match> 클래스입니다. 그런 다음 문장의 각 단어는 별도로 표시 됩니다.  
  
## <a name="example"></a>예제  
  
```  
// regex_parse.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::Text::RegularExpressions;  
  
int main( )  
{  
   int words = 0;  
   String^ pattern = "[a-zA-Z]*";  
   Console::WriteLine( "pattern : '{0}'", pattern );  
   Regex^ regex = gcnew Regex( pattern );  
  
   String^ line = "one\ttwo three:four,five six  seven";     
   Console::WriteLine( "text : '{0}'", line );  
   for( Match^ match = regex->Match( line );   
        match->Success; match = match->NextMatch( ) )   
   {  
      if( match->Value->Length > 0 )  
      {  
         words++;  
         Console::WriteLine( "{0}", match->Value );  
      }  
   }  
   Console::WriteLine( "Number of Words : {0}", words );  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [.NET Framework 정규식](/dotnet/standard/base-types/regular-expressions)   
 [C++/CLI를 사용한 .NET 프로그래밍(Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)