---
title: 파일 처리 및 I-O(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- .NET Framework [C++], file handling
- files [C++], .NET Framework and
- I/O [C++], .NET Framework applications
- .NET Framework [C++], I/O
- files [C++], listing files
- directories [C++], listing files
- monitoring file system events
- FileSystemWatcher class, examples
- examples [C++], monitoring file system changes
- events [C++], monitoring
- file system events [C++]
- files [C++], binary
- binary files, reading in C++
- reading text files
- text files, reading
- files [C++], retrieving information about
- FileInfo class
- binary files, writing in C++
- files [C++], binary
- files [C++], text
- text files, writing in C++
ms.assetid: 3296fd59-a83a-40d4-bd4a-6096cc13101b
ms.openlocfilehash: a1cfdc4239506f22368753d8c37765e550d9b835
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508936"
---
# <a name="file-handling-and-io-ccli"></a>파일 처리 및 I/O(C++/CLI)

.NET Framework를 사용 하는 다양 한 파일 작업을 보여 줍니다.

다음 항목에서는 네임 스페이스에 정의 된 클래스를 사용 <xref:System.IO> 하 여 다양 한 파일 작업을 수행 하는 방법을 보여 줍니다.

## <a name="enumerate-files-in-a-directory"></a><a name="enumerate"></a> 디렉터리의 파일 열거

다음 코드 예제에서는 디렉터리에서 파일 목록을 검색 하는 방법을 보여 줍니다. 또한 하위 디렉터리가 열거 됩니다. 다음 코드 예제에서는 및 메서드를 사용 하 여 <xref:System.IO.Directory.GetFiles%2A> <xref:System.IO.Directory.GetFiles%2A> <xref:System.IO.Directory.GetDirectories%2A> C:\Windows 디렉터리의 내용을 표시 합니다.

### <a name="example"></a>예제

```cpp
// enum_files.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ folder = "C:\\";
   array<String^>^ dir = Directory::GetDirectories( folder );
   Console::WriteLine("--== Directories inside '{0}' ==--", folder);
   for (int i=0; i<dir->Length; i++)
      Console::WriteLine(dir[i]);

   array<String^>^ file = Directory::GetFiles( folder );
   Console::WriteLine("--== Files inside '{0}' ==--", folder);
   for (int i=0; i<file->Length; i++)
      Console::WriteLine(file[i]);

   return 0;
}
```

## <a name="monitor-file-system-changes"></a><a name="monitor"></a> 파일 시스템 변경 내용 모니터링

다음 코드 예제에서는를 사용 하 여 <xref:System.IO.FileSystemWatcher> 생성, 변경, 삭제 또는 이름이 바뀐 파일에 해당 하는 이벤트를 등록 합니다. 파일 변경 내용에 대 한 디렉터리를 주기적으로 폴링하는 대신 클래스를 사용 <xref:System.IO.FileSystemWatcher> 하 여 변경 내용이 검색 되 면 이벤트를 발생 시킬 수 있습니다.

### <a name="example"></a>예제

```cpp
// monitor_fs.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::IO;

ref class FSEventHandler
{
public:
    void OnChanged (Object^ source, FileSystemEventArgs^ e)
    {
        Console::WriteLine("File: {0} {1}",
               e->FullPath, e->ChangeType);
    }
    void OnRenamed(Object^ source, RenamedEventArgs^ e)
    {
        Console::WriteLine("File: {0} renamed to {1}",
                e->OldFullPath, e->FullPath);
    }
};

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();

   if(args->Length < 2)
   {
      Console::WriteLine("Usage: Watcher.exe <directory>");
      return -1;
   }

   FileSystemWatcher^ fsWatcher = gcnew FileSystemWatcher( );
   fsWatcher->Path = args[1];
   fsWatcher->NotifyFilter = static_cast<NotifyFilters>
              (NotifyFilters::FileName |
               NotifyFilters::Attributes |
               NotifyFilters::LastAccess |
               NotifyFilters::LastWrite |
               NotifyFilters::Security |
               NotifyFilters::Size );

    FSEventHandler^ handler = gcnew FSEventHandler();
    fsWatcher->Changed += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Created += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Deleted += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Renamed += gcnew RenamedEventHandler(
            handler, &FSEventHandler::OnRenamed);

    fsWatcher->EnableRaisingEvents = true;

    Console::WriteLine("Press Enter to quit the sample.");
    Console::ReadLine( );
}
```

## <a name="read-a-binary-file"></a><a name="read_binary"></a> 이진 파일 읽기

다음 코드 예제에서는 네임 스페이스의 클래스 두 개 (및)를 사용 하 여 파일에서 이진 데이터를 읽는 방법을 보여 줍니다 <xref:System.IO?displayProperty=fullName> . <xref:System.IO.FileStream> <xref:System.IO.BinaryReader> <xref:System.IO.FileStream> 실제 파일을 나타냅니다. <xref:System.IO.BinaryReader> 이진 액세스를 허용 하는 스트림에 대 한 인터페이스를 제공 합니다.

이 코드 예제에서는 data bin 이라는 파일을 읽고 이진 형식의 정수를 포함 합니다. 이러한 종류의 파일에 대 한 자세한 내용은 [방법: 이진 파일 쓰기 (c + +/cli)](#write_binary)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// binary_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "data.bin";
   try
   {
      FileStream^ fs = gcnew FileStream(fileName, FileMode::Open);
      BinaryReader^ br = gcnew BinaryReader(fs);

      Console::WriteLine("contents of {0}:", fileName);
      while (br->BaseStream->Position < br->BaseStream->Length)
         Console::WriteLine(br->ReadInt32().ToString());

      fs->Close( );
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("File '{0}' not found", fileName);
      else
         Console::WriteLine("Exception: ({0})", e);
      return -1;
   }
   return 0;
}
```

## <a name="read-a-text-file"></a><a name="read_text"></a> 텍스트 파일 읽기

다음 코드 예제에서는 <xref:System.IO.StreamReader> 네임 스페이스에 정의 된 클래스를 사용 하 여 텍스트 파일을 한 번에 한 줄씩 열고 읽는 방법을 보여 줍니다 <xref:System.IO?displayProperty=fullName> . 이 클래스의 인스턴스는 텍스트 파일을 여는 데 사용 되 고, <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> 메서드는 각 줄을 검색 하는 데 사용 됩니다.

이 코드 예제에서는 textfile.txt 라는 파일을 읽고 텍스트를 포함 합니다. 이러한 종류의 파일에 대 한 자세한 내용은 [방법: 텍스트 파일 쓰기 (c + +/cli)](#write_text)를 참조 하세요.

### <a name="example"></a>예제

```cpp
// text_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";
   try
   {
      Console::WriteLine("trying to open file {0}...", fileName);
      StreamReader^ din = File::OpenText(fileName);

      String^ str;
      int count = 0;
      while ((str = din->ReadLine()) != nullptr)
      {
         count++;
         Console::WriteLine("line {0}: {1}", count, str );
      }
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("file '{0}' not found", fileName);
      else
         Console::WriteLine("problem reading file '{0}'", fileName);
   }

   return 0;
}
```

## <a name="retrieve-file-information"></a><a name="retrieve"></a> 파일 정보 검색

다음 코드 예제에서는 클래스를 보여 줍니다 <xref:System.IO.FileInfo> . 파일의 이름을 사용 하는 경우이 클래스를 사용 하 여 파일 크기, 디렉터리, 전체 이름, 만든 날짜 및 시간, 마지막 수정 날짜와 같은 파일에 대 한 정보를 검색할 수 있습니다.

이 코드는 Notepad.exe에 대 한 파일 정보를 검색 합니다.

### <a name="example"></a>예제

```cpp
// file_info.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();
   if (args->Length < 2)
   {
      Console::WriteLine("\nUSAGE : file_info <filename>\n\n");
      return -1;
   }

   FileInfo^ fi = gcnew FileInfo( args[1] );

   Console::WriteLine("file size: {0}", fi->Length );

   Console::Write("File creation date:  ");
   Console::Write(fi->CreationTime.Month.ToString());
   Console::Write(".{0}", fi->CreationTime.Day.ToString());
   Console::WriteLine(".{0}", fi->CreationTime.Year.ToString());

   Console::Write("Last access date:  ");
   Console::Write(fi->LastAccessTime.Month.ToString());
   Console::Write(".{0}", fi->LastAccessTime.Day.ToString());
   Console::WriteLine(".{0}", fi->LastAccessTime.Year.ToString());

   return 0;
}
```

## <a name="write-a-binary-file"></a><a name="write_binary"></a> 이진 파일 작성

다음 코드 예제에서는 파일에 이진 데이터를 쓰는 방법을 보여 줍니다. 네임 스페이스의 클래스 두 개 <xref:System.IO> (및)가 사용 됩니다. <xref:System.IO.FileStream> <xref:System.IO.BinaryWriter> <xref:System.IO.FileStream> 는 실제 파일을 나타내며,는 <xref:System.IO.BinaryWriter> 이진 액세스를 허용 하는 스트림에 대 한 인터페이스를 제공 합니다.

다음 코드 예제에서는 정수를 포함 하는 파일을 이진 형식으로 씁니다. [방법: 이진 파일 읽기 (c + +/cli)](#read_binary)의 코드를 사용 하 여이 파일을 읽을 수 있습니다.

### <a name="example"></a>예제

```cpp
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

## <a name="write-a-text-file"></a><a name="write_text"></a> 텍스트 파일 작성

다음 코드 예제에서는 <xref:System.IO.StreamWriter> 네임 스페이스에 정의 된 클래스를 사용 하 여 텍스트 파일을 만들고 텍스트 파일에 텍스트를 쓰는 방법을 보여 줍니다 <xref:System.IO> . <xref:System.IO.StreamWriter>생성자는 만들 파일의 이름을 사용 합니다. 파일이 있으면이 파일을 덮어씁니다 (True를 두 번째 생성자 인수로 전달 하지 않는 한 <xref:System.IO.StringWriter> ).

그런 다음 및 함수를 사용 하 여 파일을 정리 합니다 <xref:System.IO.StreamWriter.Write%2A> <xref:System.IO.TextWriter.WriteLine%2A> .

### <a name="example"></a>예제

```cpp
// text_write.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";

   StreamWriter^ sw = gcnew StreamWriter(fileName);
   sw->WriteLine("A text file is born!");
   sw->Write("You can use WriteLine");
   sw->WriteLine("...or just Write");
   sw->WriteLine("and do {0} output too.", "formatted");
   sw->WriteLine("You can also send non-text objects:");
   sw->WriteLine(DateTime::Now);
   sw->Close();
   Console::WriteLine("a new file ('{0}') has been written", fileName);

   return 0;
}
```

## <a name="see-also"></a>참고 항목

[C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[파일 및 스트림 I/O](/dotnet/standard/io/index)<br/>
[System.IO 네임 스페이스](/dotnet/api/system.io)
