---
title: 유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수
description: 유니버설 Windows 플랫폼 앱에서 지원 되지 않는 CRT 함수에 대 한 참조 가이드입니다.
ms.date: 04/16/2020
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
ms.openlocfilehash: 793283a5c20f04e58de22fcfca5ede1926de369c
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041837"
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수

UWP (유니버설 Windows 플랫폼) 앱을 빌드할 때는 대부분 CRT (C 런타임) 함수를 사용할 수 없습니다. 경우에 따라 해결 방법을 사용할 수 있습니다. 예를 들어 Windows 런타임 또는 Win32 Api를 사용할 수 있습니다. 다른 경우에는 해당 기능이 나 지원 Api가 UWP 앱에 적용 되지 않기 때문에 CRT 함수가 금지 되었습니다. Windows 런타임에 대해 지원 되는 대체 방법을 찾으려면 [UWP 앱에서 Windows api에](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)대 한 대체 항목을 참조 하세요.

다음 표에서는 UWP 앱을 빌드할 때 사용할 수 없는 CRT 함수를 나열 합니다. 적용 되는 해결 방법을 나타냅니다.

## <a name="unsupported-crt-functions"></a>지원되지 않는 CRT 함수

| 기능 | Description | 해결 방법 |
|-|-|-|
|`_beep` `_sleep` `_seterrormode`|이들 함수는 이전 버전 CRT에서 더 이상 사용되지 않습니다. 또한 해당 Win32 API는 UWP 앱에 사용할 수 없습니다.|해결 방법이 없습니다.|
|`chdir` `_chdrive` `getcwd`|이들 함수는 더 이상 사용되지 않거나 스레드로부터 안전하지 않습니다.|`_chdir` `_getcwd` 및 관련 함수를 사용 합니다.|
|`_cgets` `_cgets_s` `_cgetws` `_cgetws_s` `_cprintf` `_cprintf_l` `_cprintf_p` `_cprintf_p_l` `_cprintf_s` `_cprintf_s_l` `_cputs` `_cputws` `_cscanf` `_cscanf_l` `_cscanf_s` `_cscanf_s_l` `_cwait` `_cwprintf` `_cwprintf_l` `_cwprintf_p` `_cwprintf_p_l` `_cwprintf_s` `_cwprintf_s_l` `_cwscanf` `_cwscanf_l` `_cwscanf_s` `_cwscanf_s_l` `_vcprintf` `_vcprintf_l` `_vcprintf_p` `_vcprintf_p_l` `_vcprintf_s` `_vcprintf_s_l` `_vcwprintf` `_vcwprintf_l` `_vcwprintf_p` `_vcwprintf_p_l` `_vcwprintf_s` `_vcwprintf_s_l` `_getch` `_getch_nolock` `_getche` `_getche_nolock` `_getwch` `_getwch_nolock` `_getwche` `_getwche_nolock` `_putch` `_putch_nolock` `_putwch` `_putwch_nolock` `_ungetch` `_ungetch_nolock` `_ungetwch` `_ungetwch_nolock` `_kbhit` `kbhit` `putch` `cgets` `cprintf` `cputs` `cscanf` `cwait` `getch` `getche` `ungetch`|이들 함수는 콘솔에서 바로 읽고 쓰는 데 사용됩니다. UWP 앱은 GUI 전용이고 콘솔을 지원하지 않습니다.|해결 방법이 없습니다.|
|`getpid` `_getpid` | 이러한 함수는 사용되지 않습니다.|Win32 API `GetCurrentProcessId`를 사용합니다.|
|`_getdiskfree`|사용할 수 없습니다.|Win32 API `GetDiskFreeSpaceExW`를 사용합니다.|
|`_getdrive` `_getdrives`|해당 API는 UWP 앱에 사용할 수 없습니다.|해결 방법이 없습니다.|
|`_inp` `_inpd` `_inpw` `_outp` `_outpd` `_outpw` `inp` `inpd` `inpw` `outp` `outpd` `outpw`|포트 IO는 UWP 앱에서 지원되지 않습니다.|해결 방법이 없습니다.|
|`_ismbcalnum` `_ismbcalnum_l` `_ismbcalpha` `_ismbcalpha_l` `_ismbcdigit` `_ismbcdigit_l` `_ismbcgraph` `_ismbcgraph_l` `_ismbchira` `_ismbchira_l` `_ismbckata` `_ismbckata_l` `_ismbcl0` `_ismbcl0_l` `_ismbcl1` `_ismbcl1_l` `_ismbcl2` `_ismbcl2_l` `_ismbclegal` `_ismbclegal_l` `_ismbclower` `_ismbclower_l` `_ismbcprint` `_ismbcprint_l` `_ismbcpunct` `_ismbcpunct_l` `_ismbcspace` `_ismbcspace_l` `_ismbcsymbol` `_ismbcsymbol_l` `_ismbcupper` `_ismbcupper_l` `_mbbtombc` `_mbbtombc_l` `_mbbtype` `_mbbtype_l` `_mbccpy` `_mbccpy_l` `_mbccpy_s` `_mbccpy_s_l` `_mbcjistojms` `_mbcjistojms_l` `_mbcjmstojis` `_mbcjmstojis_l` `_mbclen` `_mbclen_l` `_mbctohira` `_mbctohira_l` `_mbctokata` `_mbctokata_l` `_mbctolower` `_mbctolower_l` `_mbctombb` `_mbctombb_l` `_mbctoupper` `_mbctoupper_l` `_mbsbtype` `_mbsbtype_l` `_mbscat` `_mbscat_l` `_mbscat_s` `_mbscat_s_l` `_mbschr` `_mbschr_l` `_mbscmp` `_mbscmp_l` `_mbscoll` `_mbscoll_l` `_mbscpy` `_mbscpy_l` `_mbscpy_s` `_mbscpy_s_l` `_mbscspn` `_mbscspn_l` `_mbsdec` `_mbsdec_l` `_mbsicmp` `_mbsicmp_l` `_mbsicoll` `_mbsicoll_l` `_mbsinc` `_mbsinc_l` `_mbslen` `_mbslen_l` `_mbslwr` `_mbslwr_l` `_mbslwr_s` `_mbslwr_s_l` `_mbsnbcat` `_mbsnbcat_l` `_mbsnbcat_s` `_mbsnbcat_s_l` `_mbsnbcmp` `_mbsnbcmp_l` `_mbsnbcnt` `_mbsnbcnt_l` `_mbsnbcoll` `_mbsnbcoll_l` `_mbsnbcpy` `_mbsnbcpy_l` `_mbsnbcpy_s` `_mbsnbcpy_s_l` `_mbsnbicmp` `_mbsnbicmp_l` `_mbsnbicoll` `_mbsnbicoll_l` `_mbsnbset` `_mbsnbset_l` `_mbsnbset_s` `_mbsnbset_s_l` `_mbsncat` `_mbsncat_l` `_mbsncat_s` `_mbsncat_s_l` `_mbsnccnt` `_mbsnccnt_l` `_mbsncmp` `_mbsncmp_l` `_mbsncoll` `_mbsncoll_l` `_mbsncpy` `_mbsncpy_l` `_mbsncpy_s` `_mbsncpy_s_l` `_mbsnextc` `_mbsnextc_l` `_mbsnicmp` `_mbsnicmp_l` `_mbsnicoll` `_mbsnicoll_l` `_mbsninc` `_mbsninc_l` `_mbsnlen` `_mbsnlen_l` `_mbsnset` `_mbsnset_l` `_mbsnset_s` `_mbsnset_s_l` `_mbspbrk` `_mbspbrk_l` `_mbsrchr` `_mbsrchr_l` `_mbsrev` `_mbsrev_l` `_mbsset` `_mbsset_l` `_mbsset_s` `_mbsset_s_l` `_mbsspn` `_mbsspn_l` `_mbsspnp` `_mbsspnp_l` `_mbsstr` `_mbsstr_l` `_mbstok` `_mbstok_l` `_mbstok_s` `_mbstok_s_l` `_mbsupr` `_mbsupr_l` `_mbsupr_s` `_mbsupr_s_l` `is_wctype`|멀티바이트 문자열은 UWP 앱에서 지원되지 않습니다.|대신 유니코드 문자열을 사용합니다.|
|`_pclose` `_pipe` `_popen` `_wpopen`|파이프 기능은 UWP 앱에 사용할 수 없습니다.|해결 방법이 없습니다.|
|`_resetstkoflw`|지원 Win32 API는 UWP 앱에 사용할 수 없습니다.|해결 방법이 없습니다.|
|`_getsystime` `_setsystime`|이들 API는 이전 CRT 버전에서 더 이상 사용되지 않습니다. 또한 사용자는 권한이 없으므로 UWP 앱에서 시스템 시간을 설정할 수 없습니다.|시스템 시간만 가져오려면 Win32 API `GetSystemTime`을 사용합니다. 시스템 시간을 설정할 수 없습니다.|
|`_environ``_putenv` `_putenv_s` `_searchenv` `_searchenv_s` `_dupenv_s` `_wputenv` `_wputenv_s` `_wsearchenv` getenv getenv_s `_wdupenv_s` `_wenviron` `_wgetenv` `_wgetenv_s` putenv `_wsearchenv_s``tzset`|환경 변수는 UWP 앱에 사용할 수 없습니다.|해결 방법이 없습니다. 표준 시간대를 설정 하려면를 사용 `_tzset` 합니다.|
|`_loaddll` `_getdllprocaddr` `_unloaddll`|이들 함수는 이전 CRT 버전에서 더 이상 사용되지 않습니다. 또한 사용자는 같은 응용 프로그램 패키지의 Dll을 제외 하 고 Dll을 로드할 수 없습니다.|Win32 API `LoadPackagedLibrary`, `GetProcAddress`및 `FreeLibrary` 를 사용하여 패키지된 DLL을 로드 및 사용합니다.|
|`_wexecl` `_wexecle` `_wexeclp` `_wexeclpe` `_wexecv` `_wexecve` `_wexecvp` `_wexecvpe` `_execl` `_execle` `_execlp` `_execlpe` `_execv` `_execve` `_execvp` `_execvpe` `_spawnl` `_spawnle` `_spawnlp` `_spawnlpe` `_spawnv` `_spawnve` `_spawnvp` `_spawnvpe` `_wspawnl` `_wspawnle` `_wspawnlp` `_wspawnlpe` `_wspawnv` `_wspawnve` `_wspawnvp` `_wspawnvpe` `_wsystem` `execl` `execle` `execlp` `execlpe` `execv` `execve` `execvp` `execvpe` `spawnl` `spawnle` `spawnlp` `spawnlpe` `spawnv` `spawnve` `spawnvp` `spawnvpe` `system`|이 기능은 UWP 앱에서 사용할 수 없습니다. UWP 앱은 다른 UWP 앱이나 데스크톱 앱을 호출할 수 없습니다.|해결 방법이 없습니다.|
|`_heapwalk` `_heapadd` `_heapchk` `_heapset` `_heapused`|일반적으로 이들 기능은 힙 작업을 하는 데 사용됩니다. 그러나 해당 Win32 API는 UWP 앱에서 지원되지 않습니다. 또한 앱에서 더 이상 전용 힙을 만들거나 사용할 수 없습니다.|해결 방법이 없습니다. 그러나 `_heapwalk` 은 DEBUG CRT에서 디버깅 목적으로만 사용할 수 있습니다. 이러한 함수는 Microsoft Store 업로드 된 앱에서 사용할 수 없습니다.|

다음 함수는 UWP 앱 용 CRT에서 사용할 수 있습니다. 그러나 해당 하는 Win32 또는 Windows 런타임 Api를 사용할 수 없는 경우 (예: 많은 코드 베이스를 이식 하는 경우에만) 사용 합니다.

| Functions | 해결 방법 |
|-|-|
|단일 바이트 문자열 함수 - 예: `strcat`, `strcpy`, `strlwr`등.|노출 되는 모든 Win32 Api 및 Windows 런타임 Api는 유니코드 문자 집합만 사용 하므로 UWP 앱을 엄격 하 게 유니코드로 만듭니다.  단일 바이트 함수는 많은 코드 베이스를 이식 하기 위해 남아 있지만 그렇지 않은 경우에는 피해 야 합니다. 가능한 경우 대신 해당 와이드 문자 함수를 사용 해야 합니다.|
|스트림 IO 및 하위 수준 파일 IO 함수 - 예: `fopen`, `open`등.|이러한 함수는 UWP 앱에 권장 되지 않는 동기식입니다. UWP 앱에서는 UI 스레드 잠금을 방지하기 위해 비동기 API를 사용하여 파일을 열고, 읽고, 씁니다. 해당 API의 예제는 `Windows::Storage::FileIO` 클래스의 예제입니다.|

## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Windows 8.x 스토어 앱 및 Windows Phone 8.x 앱

이전에 언급 한 Api 및 다음 Api는 Windows 8.x 스토어 앱 및 Windows Phone 8.x 앱에서 사용할 수 없습니다.

| Functions | Description | 해결 방법 |
|-|-|-|
|`_beginthread` `_beginthreadex` `_endthread` `_endthreadex`|스레딩 Win32 API는 Windows 8.x 스토어 앱에서 사용할 수 없습니다.|대신 `Windows Runtime Windows::System::Threading::ThreadPool` 또는 `concurrency::task` 를 사용합니다.|
|`_chdir` `_wchdir` `_getcwd` `_getdcwd` `_wgetcwd` `_wgetdcwd`|작업 디렉터리 개념은 Windows 8.x 스토어 앱에 적용되지 않습니다.|대신 전체 경로를 사용합니다.|
|`_isleadbyte_l` `_ismbbalnum`, `_ismbbalnum_l`, `_ismbbalpha`, `_ismbbalpha` `_ismbbalpha_l` `_ismbbgraph` `_ismbbgraph_l` `_ismbbkalnum` `_ismbbkalnum_l` `_ismbbkana` `_ismbbkana_l` `_ismbbkprint` `_ismbbkprint_l` `_ismbbkpunct` `_ismbbkpunct_l` `_ismbblead` `_ismbblead_l` `_ismbbprint` `_ismbbprint_l` `_ismbbpunct` `_ismbbpunct_l` `_ismbbtrail` `_ismbbtrail_l` `_ismbslead` `_ismbslead_l` `_ismbstrail` `_ismbstrail_l` `_mbsdup` `isleadbyte`|멀티바이트 문자열은 Windows 8.x 스토어 앱에서 지원되지 않습니다.|대신 유니코드 문자열을 사용합니다.|
|`_tzset`|환경 변수는 Windows 8.x 스토어 앱에 사용할 수 없습니다.|해결 방법이 없습니다.|
|`_get_heap_handle`, `_heapmin`|해당 Win32 API는 Windows 8.x 스토어 앱에서 지원되지 않습니다. 또한 앱에서 더 이상 전용 힙을 만들 수 없습니다.|해결 방법이 없습니다. 그러나 ``_get_heap_handle`` 은 DEBUG CRT에서 디버깅 목적으로만 사용할 수 있습니다.|
