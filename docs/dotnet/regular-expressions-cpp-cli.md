---
description: '자세한 정보: 정규식 (c + +/CLI)'
title: 정규식(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- regular expressions [C++]
- .NET Framework [C++], regular expressions
- regular expressions [C++], about regular expressions
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- Split method, parsing strings
- strings [C++], parsing
- substrings, simple matches
- searching, exact substring matches
- strings [C++], exact substring matching
- regular expressions [C++], simple matching
- IsMatch method
- strings [C++], extracting data from
- formatted strings [C++]
- regular expressions [C++], extracting data fields
- data [C++], extracting from strings
- regular expressions [C++], rearranging data
- data [C++], rearranging
- search and replace
- Replace method
- regular expressions [C++], search and replace
- strings [C++], formatting
- data [C++], formatting
- regular expressions [C++], validating data formatting
ms.assetid: 838bab49-0dbc-4089-a604-ef146269ef5a
ms.openlocfilehash: 429a121ec7acad46437a344b089f5c6a1ce4243b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245813"
---
# <a name="regular-expressions-ccli"></a>정규식(C++/CLI)

.NET Framework에서 정규식 클래스를 사용 하는 다양 한 문자열 작업을 보여 줍니다.

다음 항목에서는 .NET Framework 네임 스페이스를 사용 하는 <xref:System.Text.RegularExpressions> 방법, 즉 메서드를 사용 <xref:System.String.Split%2A?displayProperty=fullName> 하 여 문자열을 검색, 구문 분석 및 수정 하는 방법을 보여 줍니다.

## <a name="parse-strings-using-regular-expressions"></a><a name="parse_regex"></a> 정규식을 사용 하 여 문자열 구문 분석

다음 코드 예제에서는 <xref:System.Text.RegularExpressions.Regex> 네임 스페이스에서 클래스를 사용 하 여 간단한 문자열을 구문 분석 하는 방법을 보여 줍니다 <xref:System.Text.RegularExpressions?displayProperty=fullName> . 여러 형식의 word delineators을 포함 하는 문자열을 생성 합니다. 그런 다음 클래스와 함께 클래스를 사용 하 여 문자열을 구문 분석 합니다 <xref:System.Text.RegularExpressions.Regex> <xref:System.Text.RegularExpressions.Match> . 그러면 문장의 각 단어가 별도로 표시 됩니다.

### <a name="example"></a>예제

```cpp
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

## <a name="parse-strings-using-the-split-method"></a><a name="parse_split"></a> Split 메서드를 사용 하 여 문자열 구문 분석

다음 코드 예제에서는 메서드를 사용 하 여 <xref:System.String.Split%2A?displayProperty=fullName> 문자열에서 각 단어를 추출 하는 방법을 보여 줍니다. 여러 형식의 word delineators을 포함 하는 문자열은 생성 된 다음 <xref:System.String.Split%2A> delineators의 목록과 함께를 호출 하 여 구문 분석 됩니다. 그러면 문장의 각 단어가 별도로 표시 됩니다.

### <a name="example"></a>예제

```cpp
// regex_split.cpp
// compile with: /clr
using namespace System;

int main()
{
   String^ delimStr = " ,.:\t";
   Console::WriteLine( "delimiter : '{0}'", delimStr );
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ words;
   String^ line = "one\ttwo three:four,five six seven";

   Console::WriteLine( "text : '{0}'", line );
   words = line->Split( delimiter );
   Console::WriteLine( "Number of Words : {0}", words->Length );
   for (int word=0; word<words->Length; word++)
      Console::WriteLine( "{0}", words[word] );

   return 0;
}
```

## <a name="use-regular-expressions-for-simple-matching"></a><a name="regex_simple"></a> 단순 일치에 정규식 사용

다음 코드 예제에서는 정규식을 사용 하 여 정확히 일치 하는 부분 문자열을 찾습니다. 검색은 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> 두 문자열을 입력으로 사용 하는 정적 메서드를 통해 수행 됩니다. 첫 번째는 검색할 문자열이 고, 두 번째는 검색할 패턴입니다.

### <a name="example"></a>예제

```cpp
// regex_simple.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
   array<String^>^ sentence =
   {
      "cow over the moon",
      "Betsy the Cow",
      "cowering in the corner",
      "no match here"
   };

   String^ matchStr = "cow";
   for (int i=0; i<sentence->Length; i++)
   {
      Console::Write( "{0,24}", sentence[i] );
      if ( Regex::IsMatch( sentence[i], matchStr,
                     RegexOptions::IgnoreCase ) )
         Console::WriteLine("  (match for '{0}' found)", matchStr);
      else
         Console::WriteLine("");
   }
   return 0;
}
```

## <a name="use-regular-expressions-to-extract-data-fields"></a><a name="regex_extract"></a> 정규식을 사용 하 여 데이터 필드 추출

다음 코드 예제에서는 정규식을 사용 하 여 서식이 지정 된 문자열에서 데이터를 추출 하는 방법을 보여 줍니다. 다음 코드 예제에서는 클래스를 사용 하 여 <xref:System.Text.RegularExpressions.Regex> 전자 메일 주소에 해당 하는 패턴을 지정 합니다. 이 patter에는 각 전자 메일 주소의 사용자 및 호스트 이름 부분을 검색 하는 데 사용할 수 있는 필드 식별자가 포함 되어 있습니다. <xref:System.Text.RegularExpressions.Match>클래스는 실제 패턴 일치를 수행 하는 데 사용 됩니다. 지정 된 전자 메일 주소가 유효 하면 사용자 이름 및 호스트 이름이 추출 되어 표시 됩니다.

### <a name="example"></a>예제

```cpp
// Regex_extract.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
    array<String^>^ address=
    {
        "jay@southridgevideo.com",
        "barry@adatum.com",
        "treyresearch.net",
        "karen@proseware.com"
    };

    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");

    for (int i=0; i<address->Length; i++)
    {
        Match^ m = emailregex->Match( address[i] );
        Console::Write("\n{0,25}", address[i]);

        if ( m->Success )
        {
            Console::Write("   User='{0}'",
            m->Groups["user"]->Value);
            Console::Write("   Host='{0}'",
            m->Groups["host"]->Value);
        }
        else
            Console::Write("   (invalid email address)");
        }

    Console::WriteLine("");
    return 0;
}
```

## <a name="use-regular-expressions-to-rearrange-data"></a><a name="regex_rearrange"></a> 정규식을 사용 하 여 데이터 다시 정렬

다음 코드 예제에서는 .NET Framework 정규식을 사용 하 여 데이터를 다시 정렬 하거나 서식을 다시 지정 하는 방법을 보여 줍니다. 다음 코드 예제에서는 및 클래스를 사용 하 여 <xref:System.Text.RegularExpressions.Regex> <xref:System.Text.RegularExpressions.Match> 문자열에서 성과 이름을 추출 하 고 이러한 이름 요소를 역순으로 표시 합니다.

<xref:System.Text.RegularExpressions.Regex>클래스는 데이터의 현재 형식을 설명 하는 정규식을 생성 하는 데 사용 됩니다. 두 이름은 쉼표로 구분 되는 것으로 간주 되며 쉼표를 기준으로 공백을 원하는 만큼 사용할 수 있습니다. <xref:System.Text.RegularExpressions.Match>그런 다음 메서드를 사용 하 여 각 문자열을 분석 합니다. 성공 하면 개체에서 성과 이름이 검색 되어 <xref:System.Text.RegularExpressions.Match> 표시 됩니다.

### <a name="example"></a>예제

```cpp
// regex_reorder.cpp
// compile with: /clr
#using <System.dll>
using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ name =
   {
      "Abolrous, Sam",
      "Berg,Matt",
      "Berry , Jo",
      "www.contoso.com"
   };

   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");

   for ( int i=0; i < name->Length; i++ )
   {
      Console::Write( "{0,-20}", name[i] );
      Match^ m = reg->Match( name[i] );
      if ( m->Success )
      {
         String^ first = m->Groups["first"]->Value;
         String^ last = m->Groups["last"]->Value;
         Console::WriteLine("{0} {1}", first, last);
      }
      else
         Console::WriteLine("(invalid)");
   }
   return 0;
}
```

## <a name="use-regular-expressions-to-search-and-replace"></a><a name="regex_search"></a> 정규식을 사용 하 여 검색 및 바꾸기

다음 코드 예제에서는 정규식 클래스를 사용 하 여 <xref:System.Text.RegularExpressions.Regex> 검색 및 바꾸기를 수행 하는 방법을 보여 줍니다. 이 작업은 메서드를 사용 하 여 수행 됩니다 <xref:System.Text.RegularExpressions.Regex.Replace%2A> . 사용 되는 버전은 두 문자열을 입력으로 사용 합니다. 수정할 문자열 및 개체에 지정 된 패턴과 일치 하는 섹션 (있는 경우) 대신 삽입할 문자열 <xref:System.Text.RegularExpressions.Regex> 입니다.

이 코드는 문자열의 모든 숫자를 밑줄 (_)로 바꾼 다음 빈 문자열로 바꿔서 효과적으로 제거 합니다. 동일한 효과를 단일 단계로 수행할 수 있지만 여기서는 데모용으로 두 단계를 사용 합니다.

### <a name="example"></a>예제

```cpp
// regex_replace.cpp
// compile with: /clr
#using <System.dll>
using namespace System::Text::RegularExpressions;
using namespace System;

int main()
{
   String^ before = "The q43uick bro254wn f0ox ju4mped";
   Console::WriteLine("original  : {0}", before);

   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");
   String^ after = digitRegex->Replace(before, "_");
   Console::WriteLine("1st regex : {0}", after);

   Regex^ underbarRegex = gcnew Regex("_");
   String^ after2 = underbarRegex->Replace(after, "");
   Console::WriteLine("2nd regex : {0}", after2);

   return 0;
}
```

## <a name="use-regular-expressions-to-validate-data-formatting"></a><a name="regex_validate"></a> 정규식을 사용 하 여 데이터 형식 유효성 검사

다음 코드 예제에서는 정규식을 사용 하 여 문자열의 형식을 확인 하는 방법을 보여 줍니다. 다음 코드 예제에서는 문자열에 올바른 전화 번호가 포함 되어야 합니다. 다음 코드 예에서는 "\d {3} -\d-\d" 문자열을 사용 하 여 {3} {4} 각 필드가 올바른 전화 번호를 나타내는지 나타냅니다. 문자열의 "d"는 숫자를 나타내고 각 "d" 뒤의 인수는 표시 되어야 하는 자릿수를 나타냅니다. 이 경우 숫자를 대시로 구분 해야 합니다.

### <a name="example"></a>예제

```cpp
// regex_validate.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ number =
   {
      "123-456-7890",
      "444-234-22450",
      "690-203-6578",
      "146-893-232",
      "146-839-2322",
      "4007-295-1111",
      "407-295-1111",
      "407-2-5555",
   };

   String^ regStr = "^\\d{3}-\\d{3}-\\d{4}$";

   for ( int i = 0; i < number->Length; i++ )
   {
      Console::Write( "{0,14}", number[i] );

      if ( Regex::IsMatch( number[i], regStr ) )
         Console::WriteLine(" - valid");
      else
         Console::WriteLine(" - invalid");
   }
   return 0;
}
```

## <a name="related-sections"></a>관련 단원

[.NET Framework 정규식](/dotnet/standard/base-types/regular-expressions)

## <a name="see-also"></a>참고 항목

[C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
