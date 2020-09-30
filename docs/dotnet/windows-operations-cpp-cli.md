---
title: Windows 작업(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows [C++], Windows-specific tasks
- .NET Framework [C++], Windows operations
- Visual C++, Windows operations
- Windows operations [C++]
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
- Visual C++, user interactive state
- user interactive state
- Visual C++, reading from Windows Registry
- registry, reading
- performance counters
- performance counters, reading Windows performance counters
- performance monitoring, Windows performance counters
- performance, counters
- counters, reading Windows performance counters
- performance
- performance monitoring
- text, retrieving from Clipboard
- Clipboard, retrieving text
- current user names
- user names, retrieving
- UserName string
- .NET Framework, version
- Version property, retrieving .NET Framework version
- computer name, retrieving
- machine name, retrieving
- computer name
- Windows [C++], version
- Windows [C++], retrieving version using Visual C++
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
- text, storing in Clipboard
- Clipboard, storing text
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: b9a75cb4-0589-4d5b-92cb-5e8be42b4ac0
ms.openlocfilehash: 3c4ef2a69c25313ff444e0fabaea6eef2feeeee2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501658"
---
# <a name="windows-operations-ccli"></a>Windows 작업(C++/CLI)

Windows SDK를 사용 하는 다양 한 Windows 관련 작업을 보여 줍니다.

다음 항목에서는 Visual C++를 사용 하 여 Windows SDK에서 수행 되는 다양 한 Windows 작업을 보여 줍니다.

## <a name="determine-if-shutdown-has-started"></a><a name="determine_shutdown"></a> 종료가 시작 되었는지 확인

다음 코드 예제에서는 응용 프로그램 또는 .NET Framework 현재 종료 되 고 있는지 여부를 확인 하는 방법을 보여 줍니다. 이는 종료 하는 동안 시스템에서 이러한 구문을 종료 하 고 안정적으로 사용할 수 없기 때문에 .NET Framework의 정적 요소에 액세스 하는 데 유용 합니다. 먼저 속성을 확인 하 여 <xref:System.Environment.HasShutdownStarted%2A> 이러한 요소에 액세스 하지 않고 잠재적 오류를 방지할 수 있습니다.

### <a name="example"></a>예제

```cpp
// check_shutdown.cpp
// compile with: /clr
using namespace System;
int main()
{
   if (Environment::HasShutdownStarted)
      Console::WriteLine("Shutting down.");
   else
      Console::WriteLine("Not shutting down.");
   return 0;
}
```

## <a name="determine-the-user-interactive-state"></a><a name="determine_user"></a> 사용자 대화형 상태 확인

다음 코드 예제에서는 코드가 사용자 대화형 컨텍스트에서 실행 되는지 여부를 확인 하는 방법을 보여 줍니다. <xref:System.Environment.UserInteractive%2A>가 false 이면 코드가 서비스 프로세스로 실행 되거나 웹 응용 프로그램 내에서 실행 되 고,이 경우 사용자와의 상호 작용을 시도 하지 않아야 합니다.

### <a name="example"></a>예제

```cpp
// user_interactive.cpp
// compile with: /clr
using namespace System;

int main()
{
   if ( Environment::UserInteractive )
      Console::WriteLine("User interactive");
   else
      Console::WriteLine("Noninteractive");
   return 0;
}
```

## <a name="read-data-from-the-windows-registry"></a><a name="read_registry"></a> Windows 레지스트리에서 데이터 읽기

다음 코드 예제에서는 키를 사용 하 여 <xref:Microsoft.Win32.Registry.CurrentUser> Windows 레지스트리에서 데이터를 읽습니다. 먼저 메서드를 사용 하 여 하위 키를 열거 한 <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> 다음 메서드를 사용 하 여 id 하위 키를 엽니다 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> . 루트 키와 마찬가지로 각 하위 키는 클래스로 표현 됩니다 <xref:Microsoft.Win32.RegistryKey> . 마지막으로 새 <xref:Microsoft.Win32.RegistryKey> 개체는 키/값 쌍을 열거 하는 데 사용 됩니다.

### <a name="example"></a>예제

```cpp
// registry_read.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main( )
{
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );

   Console::WriteLine("Subkeys within CurrentUser root key:");
   for (int i=0; i<key->Length; i++)
   {
      Console::WriteLine("   {0}", key[i]);
   }

   Console::WriteLine("Opening subkey 'Identities'...");
   RegistryKey^ rk = nullptr;
   rk = Registry::CurrentUser->OpenSubKey("Identities");
   if (rk==nullptr)
   {
      Console::WriteLine("Registry key not found - aborting");
      return -1;
   }

   Console::WriteLine("Key/value pairs within 'Identities' key:");
   array<String^>^ name = rk->GetValueNames( );
   for (int i=0; i<name->Length; i++)
   {
      String^ value = rk->GetValue(name[i])->ToString();
      Console::WriteLine("   {0} = {1}", name[i], value);
   }

   return 0;
}
```

### <a name="remarks"></a>설명

<xref:Microsoft.Win32.Registry>클래스는 단순히의 정적 인스턴스에 대 한 컨테이너입니다 <xref:Microsoft.Win32.RegistryKey> . 각 인스턴스는 루트 레지스트리 노드를 나타냅니다. 인스턴스는 <xref:Microsoft.Win32.Registry.ClassesRoot> ,, <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser> , <xref:Microsoft.Win32.Registry.LocalMachine> 및 <xref:Microsoft.Win32.Registry.Users> 입니다.

정적이 고 클래스 내의 개체는 <xref:Microsoft.Win32.Registry> 읽기 전용입니다. 또한 <xref:Microsoft.Win32.RegistryKey> 레지스트리 개체의 내용에 액세스 하기 위해 만든 클래스의 인스턴스도 읽기 전용입니다. 이 동작을 재정의 하는 방법에 대 한 예제는 [방법: Windows 레지스트리에 데이터 쓰기 (c + +/cli)](#write_data)를 참조 하세요.

클래스에는 및 라는 두 개의 추가 개체가 있습니다. <xref:Microsoft.Win32.Registry> <xref:Microsoft.Win32.Registry.DynData> <xref:Microsoft.Win32.Registry.PerformanceData> 둘 다 클래스의 인스턴스입니다 <xref:Microsoft.Win32.RegistryKey> . <xref:Microsoft.Win32.Registry.DynData>개체는 windows 98 및 Windows Me 에서만 지원 되는 동적 레지스트리 정보를 포함 합니다. 개체를 사용 하 여 <xref:Microsoft.Win32.Registry.PerformanceData> Windows 성능 모니터링 시스템을 사용 하는 응용 프로그램에 대 한 성능 카운터 정보에 액세스할 수 있습니다. <xref:Microsoft.Win32.Registry.PerformanceData>이 노드는 레지스트리에 실제로 저장 되지 않으므로 Regedit.exe를 사용 하 여 볼 수 없는 정보를 나타냅니다.

## <a name="read-windows-performance-counters"></a><a name="read_performance"></a> Windows 성능 카운터 읽기

일부 응용 프로그램 및 Windows 하위 시스템은 Windows 성능 시스템을 통해 성능 데이터를 노출 합니다. 이러한 카운터는 <xref:System.Diagnostics.PerformanceCounterCategory> <xref:System.Diagnostics.PerformanceCounter> 네임 스페이스에 상주 하는 및 클래스를 사용 하 여 액세스할 수 있습니다 <xref:System.Diagnostics?displayProperty=fullName> .

다음 코드 예제에서는 이러한 클래스를 사용 하 여 Windows에서 업데이트 된 카운터를 검색 하 고 표시 하 여 프로세서가 사용 중인 시간의 백분율을 나타냅니다.

> [!NOTE]
> 이 예제를 Windows Vista에서 실행하려면 관리 권한이 필요합니다.

### <a name="example"></a>예제

```cpp
// processor_timer.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Diagnostics;
using namespace System::Timers;

ref struct TimerObject
{
public:
   static String^ m_instanceName;
   static PerformanceCounter^ m_theCounter;

public:
   static void OnTimer(Object^ source, ElapsedEventArgs^ e)
   {
      try
      {
         Console::WriteLine("CPU time used: {0,6} ",
          m_theCounter->NextValue( ).ToString("f"));
      }
      catch(Exception^ e)
      {
         if (dynamic_cast<InvalidOperationException^>(e))
         {
            Console::WriteLine("Instance '{0}' does not exist",
                  m_instanceName);
            return;
         }
         else
         {
            Console::WriteLine("Unknown exception... ('q' to quit)");
            return;
         }
      }
   }
};

int main()
{
   String^ objectName = "Processor";
   String^ counterName = "% Processor Time";
   String^ instanceName = "_Total";

   try
   {
      if ( !PerformanceCounterCategory::Exists(objectName) )
      {
         Console::WriteLine("Object {0} does not exist", objectName);
         return -1;
      }
   }
   catch (UnauthorizedAccessException ^ex)
   {
      Console::WriteLine("You are not authorized to access this information.");
      Console::Write("If you are using Windows Vista, run the application with ");
      Console::WriteLine("administrative privileges.");
      Console::WriteLine(ex->Message);
      return -1;
   }

   if ( !PerformanceCounterCategory::CounterExists(
          counterName, objectName) )
   {
      Console::WriteLine("Counter {0} does not exist", counterName);
      return -1;
   }

   TimerObject::m_instanceName = instanceName;
   TimerObject::m_theCounter = gcnew PerformanceCounter(
          objectName, counterName, instanceName);

   System::Timers::Timer^ aTimer = gcnew System::Timers::Timer();
   aTimer->Elapsed += gcnew ElapsedEventHandler(&TimerObject::OnTimer);
   aTimer->Interval = 1000;
   aTimer->Enabled = true;
   aTimer->AutoReset = true;

   Console::WriteLine("reporting CPU usage for the next 10 seconds");
   Thread::Sleep(10000);
   return 0;
}
```

## <a name="retrieve-text-from-the-clipboard"></a><a name="retrieve_text"></a> 클립보드에서 텍스트 검색

다음 코드 예제에서는 멤버 함수를 사용 하 여 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 인터페이스에 대 한 포인터를 반환 합니다 <xref:System.Windows.Forms.IDataObject> . 그런 다음 데이터의 형식에 대해이 인터페이스를 쿼리하고 실제 데이터를 검색 하는 데 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// read_clipboard.cpp
// compile with: /clr
#using <system.dll>
#using <system.Drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main( )
{
   IDataObject^ data = Clipboard::GetDataObject( );

   if (data)
   {
      if (data->GetDataPresent(DataFormats::Text))
      {
         String^ text = static_cast<String^>
           (data->GetData(DataFormats::Text));
         Console::WriteLine(text);
      }
      else
         Console::WriteLine("Nontext data is in the Clipboard.");
   }
   else
   {
      Console::WriteLine("No data was found in the Clipboard.");
   }

   return 0;
}
```

## <a name="retrieve-the-current-username"></a><a name="retrieve_current"></a> 현재 사용자 이름을 검색 합니다.

다음 코드 예제에서는 현재 사용자 이름 (Windows에 로그인 한 사용자의 이름)을 검색 하는 방법을 보여 줍니다. 이름은 <xref:System.Environment.UserName%2A> 네임 스페이스에 정의 된 문자열에 저장 됩니다 <xref:System.Environment> .

### <a name="example"></a>예제

```cpp
// username.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);
   return 0;
}
```

## <a name="retrieve-the-net-framework-version"></a><a name="retrieve_dotnet"></a> .NET Framework 버전 검색

다음 코드 예제에서는 속성을 사용 하 여 현재 설치 된 .NET Framework 버전을 확인 하는 방법을 보여 줍니다 <xref:System.Environment.Version%2A> .이 속성은 <xref:System.Version> 버전 정보를 포함 하는 개체에 대 한 포인터입니다.

### <a name="example"></a>예제

```cpp
// dotnet_ver.cpp
// compile with: /clr
using namespace System;
int main()
{
   Version^ version = Environment::Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write(".NET Framework version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
            build, major, minor, revision);
   }
   return 0;
}
```

## <a name="retrieve-the-local-machine-name"></a><a name="retrieve_local"></a> 로컬 컴퓨터 이름을 검색 합니다.

다음 코드 예제에서는 로컬 컴퓨터 이름 (네트워크에 표시 되는 컴퓨터의 이름)을 검색 하는 방법을 보여 줍니다. <xref:System.Environment.MachineName%2A>네임 스페이스에 정의 된 문자열을 가져와이를 수행할 수 있습니다 <xref:System.Environment> .

### <a name="example"></a>예제

```cpp
// machine_name.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nMachineName: {0}", Environment::MachineName);
   return 0;
}
```

## <a name="retrieve-the-windows-version"></a><a name="retrieve_version"></a> Windows 버전 검색

다음 코드 예제에서는 현재 운영 체제의 플랫폼 및 버전 정보를 검색 하는 방법을 보여 줍니다. 이 정보는 속성에 저장 되며 <xref:System.Environment.OSVersion%2A?displayProperty=fullName> 광범위 한 용어에서의 Windows 버전을 설명 하는 열거형과 <xref:System.Environment.Version%2A> 운영 체제의 정확한 빌드가 포함 된 개체로 구성 됩니다.

### <a name="example"></a>예제

```cpp
// os_ver.cpp
// compile with: /clr
using namespace System;

int main()
{
   OperatingSystem^ osv = Environment::OSVersion;
   PlatformID id = osv->Platform;
   Console::Write("Operating system: ");

   if (id == PlatformID::Win32NT)
      Console::WriteLine("Win32NT");
   else if (id == PlatformID::Win32S)
      Console::WriteLine("Win32S");
   else if (id == PlatformID::Win32Windows)
      Console::WriteLine("Win32Windows");
   else
      Console::WriteLine("WinCE");

   Version^ version = osv->Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write("OS Version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
                   build, major, minor, revision);
   }

   return 0;
}
```

## <a name="retrieve-time-elapsed-since-startup"></a><a name="retrieve_time"></a> 시작 이후 경과 된 시간 검색

다음 코드 예제에서는 틱 수 또는 Windows가 시작 된 이후 경과 된 시간 (밀리초)을 확인 하는 방법을 보여 줍니다. 이 값은 멤버에 저장 <xref:System.Environment.TickCount%2A?displayProperty=fullName> 되며 32 비트 값 이므로 24.9 일 마다 0으로 다시 설정 됩니다.

### <a name="example"></a>예제

```cpp
// startup_time.cpp
// compile with: /clr
using namespace System;

int main( )
{
   Int32 tc = Environment::TickCount;
   Int32 seconds = tc / 1000;
   Int32 minutes = seconds / 60;
   float hours = static_cast<float>(minutes) / 60;
   float days = hours / 24;

   Console::WriteLine("Milliseconds since startup: {0}", tc);
   Console::WriteLine("Seconds since startup: {0}", seconds);
   Console::WriteLine("Minutes since startup: {0}", minutes);
   Console::WriteLine("Hours since startup: {0}", hours);
   Console::WriteLine("Days since startup: {0}", days);

   return 0;
}
```

## <a name="store-text-in-the-clipboard"></a><a name="store_text"></a> 클립보드에 텍스트 저장

다음 코드 예제에서는 <xref:System.Windows.Forms.Clipboard> 네임 스페이스에 정의 된 개체를 사용 하 여 <xref:System.Windows.Forms> 문자열을 저장 합니다. 이 개체는 및의 두 멤버 함수를 제공 합니다. <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 에서 파생 된 개체를로 전송 하 여 데이터를 클립보드에 저장 <xref:System.Object> <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> 합니다.

### <a name="example"></a>예제

```cpp
// store_clipboard.cpp
// compile with: /clr
#using <System.dll>
#using <System.Drawing.dll>
#using <System.Windows.Forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main()
{
   String^ str = "This text is copied into the Clipboard.";

   // Use 'true' as the second argument if
   // the data is to remain in the clipboard
   // after the program terminates.
   Clipboard::SetDataObject(str, true);

   Console::WriteLine("Added text to the Clipboard.");

   return 0;
}
```

## <a name="write-data-to-the-windows-registry"></a><a name="write_data"></a> Windows 레지스트리에 데이터 쓰기

다음 코드 예제에서는 키를 사용 하 여 <xref:Microsoft.Win32.Registry.CurrentUser> <xref:Microsoft.Win32.RegistryKey> **소프트웨어** 키에 해당 하는 클래스의 쓰기 가능한 인스턴스를 만듭니다. <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>그런 다음 메서드를 사용 하 여 새 키를 만들고 키/값 쌍에를 추가 합니다.

### <a name="example"></a>예제

```cpp
// registry_write.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main()
{
   // The second OpenSubKey argument indicates that
   // the subkey should be writable.
   RegistryKey^ rk;
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);
   if (!rk)
   {
      Console::WriteLine("Failed to open CurrentUser/Software key");
      return -1;
   }

   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");
   if (!nk)
   {
      Console::WriteLine("Failed to create 'NewRegKey'");
      return -1;
   }

   String^ newValue = "NewValue";
   try
   {
      nk->SetValue("NewKey", newValue);
      nk->SetValue("NewKey2", 44);
   }
   catch (Exception^)
   {
      Console::WriteLine("Failed to set new values in 'NewRegKey'");
      return -1;
   }

   Console::WriteLine("New key created.");
   Console::Write("Use REGEDIT.EXE to verify ");
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");
   return 0;
}
```

### <a name="remarks"></a>설명

.NET Framework를 사용 하 여 <xref:Microsoft.Win32.Registry> <xref:Microsoft.Win32.RegistryKey> 네임 스페이스에 정의 된 및 클래스를 사용 하 여 레지스트리에 액세스할 수 있습니다 <xref:Microsoft.Win32> . **레지스트리** 클래스는 클래스의 정적 인스턴스에 대 한 컨테이너입니다 <xref:Microsoft.Win32.RegistryKey> . 각 인스턴스는 루트 레지스트리 노드를 나타냅니다. 인스턴스는 <xref:Microsoft.Win32.Registry.ClassesRoot> ,, <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser> , <xref:Microsoft.Win32.Registry.LocalMachine> 및 <xref:Microsoft.Win32.Registry.Users> 입니다.

## <a name="related-sections"></a>관련 섹션

<xref:System.Environment>

## <a name="see-also"></a>참고 항목

[C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
