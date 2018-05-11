---
title: '방법: 이진 파일 쓰기 (C + + /cli CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- binary files, writing in C++
- files [C++], binary
ms.assetid: 35d97ee6-fc7e-4c36-be18-8bbb3b44b3ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 69467b913ea76b5f5e19772ee7d0d846a363c5e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-a-binary-file-ccli"></a>방법: 이진 파일 쓰기(C++/CLI)
다음 코드 예제에서는 이진 데이터 파일에 쓰는 하는 방법을 보여 줍니다. 두 개의 클래스는 <xref:System.IO> 네임 스페이스가 사용 됩니다: <xref:System.IO.FileStream> 및 <xref:System.IO.BinaryWriter>합니다. <xref:System.IO.FileStream> 실제 파일을 나타내는 반면 <xref:System.IO.BinaryWriter> 이진 액세스를 허용 하는 스트림에 인터페이스를 제공 합니다.  
  
 다음 코드 예제에서는 이진 형식에서 정수를 포함 하는 파일을 씁니다. 이 파일의 코드를 읽을 수 있는 [하는 방법: 이진 파일 읽기 (C + + /cli CLI)](../dotnet/how-to-read-a-binary-file-cpp-cli.md)합니다.  
  
## <a name="example"></a>예제  
  
```  
// binary_write.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   array<Int32>^ data = {1, 2, 3, 10000};  
  
   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);  
   BinaryWriter^ w = gcnew BinaryWriter(fs);  
  
   try   
   {  
      Console::WriteLine("writing data to file:");  
      for (int i=0; i<data->Length; i++)  
      {  
         Console::WriteLine(data[i]);  
         w->Write(data[i]);  
      }  
   }  
   catch (Exception^)   
   {  
     Console::WriteLine("data could not be written");  
     fs->Close();  
     return -1;  
   }  
  
   fs->Close();  
   return 0;  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [파일 및 스트림 I/O](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [C++/CLI를 사용한 .NET 프로그래밍(Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)