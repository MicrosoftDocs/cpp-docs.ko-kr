---
description: '자세한 정보: ATL 클래스 및 구조체'
title: ATL 클래스 및 구조체 | Microsoft Docs
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: bfd49a6e03b285d0923c82818bef3a83ad47cc4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158896"
---
# <a name="atl-classes-and-structs"></a>ATL 클래스 및 구조체

ATL (액티브 템플릿 라이브러리)에는 다음과 같은 클래스와 구조체가 포함 되어 있습니다. 범주별로 특정 클래스를 찾으려면 [ATL 클래스 개요](../../atl/atl-class-overview.md)를 참조 하세요.

|클래스/구조체|설명|헤더 파일|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|프린터, 메타 파일 또는 ActiveX 컨트롤과 같은 다양 한 대상으로 렌더링 하는 데 사용 되는 정보를 포함 합니다.|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|ATL의 창 고 코드에 클래스 인스턴스 데이터를 포함 합니다.|atlbase.h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|ATL을 사용 하는 모든 프로젝트에서 사용 됩니다.|atlbase.h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|ATL의 COM 관련 코드에서 사용 됩니다.| atlbase.h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|의 메서드 또는 속성을 설명 하는 데 사용 되는 형식 정보를 포함 합니다.|atlcom.h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|모든 ATL 모듈에서 사용 하는 데이터를 포함 합니다.|atlbase.h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|ATL의 창 고 코드에서 사용 됩니다.|atlbase.h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|이 클래스는 문자열 변환 매크로 CA2TEX 및 CT2AEX 및 typedef CA2A에 사용 됩니다.|atlconv.h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|이 클래스는 문자열 변환 매크로 CA2CTEX 및 CT2CAEX 및 typedef CA2CA에 사용 됩니다.|atlconv.h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|이 클래스는 문자열 변환 매크로 CA2TEX, CA2CTEX, CT2WEX 및 CT2CWEX와 typedef CA2W에서 사용 됩니다.|atlconv.h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|이 클래스는 액세스 토큰에 대 한 래퍼입니다.|atlsecurity.h|
|[CAcl](../../atl/reference/cacl-class.md)|이 클래스는 ACL (액세스 제어 목록) 구조체에 대 한 래퍼입니다.|atlsecurity.h|
|[CAdapt](../../atl/reference/cadapt-class.md)|이 템플릿은 개체 주소 이외의 주소를 반환하도록 연산자 주소를 다시 정의하는 클래스를 래핑하는 데 사용됩니다.|atlcomcli.h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|이 클래스는 배열 개체를 구현 합니다.|atlcoll.h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|이 클래스는 스레드 풀의 아파트 모델 COM 서버를 구현 합니다.|atlbase.h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|이 클래스는 스레드 풀의 아파트 모델 COM 서버를 구현 하는 메서드를 제공 합니다.|atlbase.h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|이 클래스는 모든 ATL 프로젝트에서 인스턴스화됩니다.|atlcore.h|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|이 클래스는 COM 서버 모듈을 구현 합니다.|atlbase.h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|이 클래스는 디버깅 인터페이스에 대 한 지원을 제공 합니다.|atlbase.h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|이 클래스는 DLL에 대 한 모듈을 나타냅니다.|atlbase.h|
|[CAtlException](../../atl/reference/catlexception-class.md)|이 클래스는 ATL 예외를 정의 합니다.|atlexcept.h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|이 클래스는 응용 프로그램에 대 한 모듈을 나타냅니다.|atlbase.h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|이 클래스는 Windows 파일 처리 API에 대 한 씬 래퍼를 제공 합니다.|atlfile.h|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|이 클래스는 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)의 메서드에 캐스트 연산자를 추가 하 여 메모리 매핑된 파일을 나타냅니다.|atlfile.h|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|이 클래스는 메모리 매핑된 파일을 나타냅니다.|atlfile.h|
|[CAtlList](../../atl/reference/catllist-class.md)|이 클래스는 목록 개체를 만들고 관리 하는 메서드를 제공 합니다.|atlcoll.h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|이 클래스는 map 개체를 만들고 관리 하는 메서드를 제공 합니다.|atlcoll.h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|이 클래스는 여러 ATL 모듈 클래스에서 사용 하는 메서드를 제공 합니다.|atlbase.h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|이 클래스는 ATL 모듈을 구현 합니다.|atlbase.h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|이 클래스는 풍부한 미리 보기를 위해 셸에서 제공 하는 호스트 창에 배치 되는 창의 ATL 구현입니다.|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|이 클래스는 서비스를 구현 합니다.|atlbase.h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|이 클래스는 임시 파일을 만들고 사용 하기 위한 메서드를 제공 합니다.|atlfile.h|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|이 클래스는 KTM (Kernel Transaction Manager) 함수에 대 한 래퍼를 제공 합니다.|atltransactionmanager.h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|이 클래스는 ATL 창 구성 요소에 대 한 지원을 제공 합니다.|atlbase.h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|이 클래스는 스마트 포인터 개체를 나타냅니다.|atlbase.h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|이 클래스는 스마트 포인터의 배열을 생성할 때 유용한 메서드를 제공 합니다.|atlbase.h|
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|이 클래스는 스마트 포인터의 컬렉션을 만들 때 유용한 메서드, 정적 함수 및 typedef를 제공 합니다.|atlcoll.h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|이 클래스는 스마트 포인터 목록을 생성할 때 유용한 메서드를 제공 합니다.|atlcoll.h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|이 클래스는 vector new 및 delete 연산자를 사용 하는 스마트 포인터 개체를 나타냅니다.|atlbase.h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|이 클래스는 vector new 및 delete 연산자를 사용 하 여 스마트 포인터의 컬렉션을 만들 때 유용한 메서드, 정적 함수 및 typedef를 제공 합니다.|atlcoll.h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|이 클래스는 ActiveX 컨트롤을 호스트 하는 대화 상자 (모달 또는 모덜리스)를 구현 합니다.|atlwin.h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|이 클래스는 ActiveX 컨트롤을 호스트 하는 창을 조작 하기 위한 메서드를 제공 합니다.|atlwin.h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|이 클래스는 ActiveX 컨트롤을 호스트 하는 창을 조작 하기 위한 메서드를 제공 하며, 사용이 허가 된 ActiveX 컨트롤을 호스팅할 수도 있습니다.|atlwin.h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|이 클래스는 `IBindStatusCallback` 인터페이스를 구현합니다.|atlctl.h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|이 클래스는 집계 된 개체에 대해 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 을 구현 합니다.|atlcom.h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|이 클래스는 COM 메모리 루틴을 사용 하 여 메모리를 관리 하는 메서드를 제공 합니다.|atlbase.h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|이 클래스는 스레드 풀링된 EXE 모듈에서 아파트를 관리 하는 기능을 지원 합니다.|atlbase.h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|이 클래스는 임계 영역 개체의 소유권을 가져오고 해제 하는 메서드를 제공 합니다.|atlcore.h|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|ATL 7.0의 경우 `CComAutoThreadModule` 는 사용 되지 않습니다. 자세한 내용은 [atl 모듈](../../atl/atl-module-classes.md) 을 참조 하세요.|atlbase.h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|이 클래스는 Bstr에 대 한 래퍼입니다.|atlbase.h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|이 클래스는 분리 인터페이스에 대해 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 을 구현 합니다.|atlcom.h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|이 클래스는 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) 인터페이스를 구현 합니다.|atlcom.h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|이 클래스는 [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) 인터페이스를 구현 합니다.|atlcom.h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|이 클래스는 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) 인터페이스를 구현 하 고 여러 아파트에서 개체를 만들 수 있도록 합니다.|atlcom.h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|이 클래스는 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 에서 파생 되며 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 를 사용 하 여 단일 개체를 생성 합니다.|atlcom.h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|이 클래스는 클래스의 인스턴스를 만들고 해당 속성을 가져오는 메서드를 제공 합니다.|atlcom.h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|이 클래스는 복합 컨트롤을 구현 하는 데 필요한 메서드를 제공 합니다.|atlctl.h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|이 클래스는 소유자 개체의 `IUnknown`에 위임하여 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)을 구현합니다.|atlcom.h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|이 클래스는 ATL 컨트롤을 만들고 관리 하기 위한 메서드를 제공 합니다.|atlctl.h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|이 클래스는 ATL 컨트롤을 만들고 관리 하기 위한 메서드를 제공 합니다.|atlctl.h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|이 클래스는 임계 영역 개체의 소유권을 가져오고 해제 하는 메서드를 제공 합니다.|atlcore.h|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|이 클래스는 임계 영역 개체를 잠그고 잠금 해제 하는 메서드를 제공 합니다.|atlbase.h|
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|이 클래스에는 통화 개체를 만들고 관리 하기 위한 메서드 및 연산자가 있습니다.|atlcur.h|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|이 클래스는 포인터의 배열을 저장 `IUnknown` 합니다.|atlcom.h|
|[CComEnum](../../atl/reference/ccomenum-class.md)|이 클래스는 배열을 기반으로 COM 열거자 개체를 정의 합니다.|atlcom.h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|이 클래스는 열거 되는 항목이 배열에 저장 되는 COM 열거자 인터페이스에 대 한 구현을 제공 합니다.|atlcom.h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|이 클래스는 c + + 표준 라이브러리 컬렉션을 기반으로 COM 열거자 개체를 정의 합니다.|atlcom.h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|이 클래스는 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 와 동일한 메서드를 제공 하지만 임계 영역을 제공 하지 않습니다.|atlcore.h|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|이 클래스는 인터페이스 포인터와 GIT (전역 인터페이스 테이블)를 처리 하기 위한 메서드를 제공 합니다.|atlbase.h|
|[CComHeap](../../atl/reference/ccomheap-class.md)|이 클래스는 COM 메모리 할당 함수를 사용 하 여 [Iatlmemmgr](../../atl/reference/iatlmemmgr-class.md) 을 구현 합니다.|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|힙 포인터를 관리 하기 위한 스마트 포인터 클래스입니다.|atlbase.h|
|[CComModule](../../atl/reference/ccommodule-class.md)|ATL 7.0의 경우 `CComModule` 는 사용 되지 않습니다. 자세한 내용은 [atl 모듈](../../atl/atl-module-classes.md) 을 참조 하세요.|atlbase.h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|이 클래스는 변수의 값을 증가 및 감소 시키는 스레드로부터 안전한 메서드를 제공 합니다.|atlbase.h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|이 클래스는 임계 영역 잠금 또는 잠금 해제 기능 없이 변수 값을 증가 및 감소 시키는 스레드로부터 안전한 메서드를 제공 합니다.|atlbase.h|
|[CComObject](../../atl/reference/ccomobject-class.md)|이 클래스는 집계할 때를 구현 하지 않는 `IUnknown` 개체에 대해를 구현 합니다.|atlcom.h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|이 클래스는 개체를 포함 하는 모듈에 대 한 참조 횟수를 관리 `Base` 합니다.|atlcom.h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|이 클래스 `IUnknown` 는 집계 되지 않은 개체에 대해를 구현 하지만 생성자에서 모듈 잠금 수를 증가 시 지 않습니다.|atlcom.h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|이 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) 의 typedef는 서버의 기본 스레딩 모델에서 템플릿 화 합니다.|atlcom.h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|이 클래스는 집계할 수 없는 개체와 집계 된 개체 모두에 대 한 개체 참조 수 관리를 처리 하는 메서드를 제공 합니다.|atlcom.h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|이 클래스는 임시 COM 개체를 만들고의 기초 구현을 제공 `IUnknown` 합니다.|atlcom.h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|이 클래스 `IUnknown` 는 집계 되거나 집계 되지 않은 개체에 대해를 구현 합니다.|atlcom.h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|COM 인터페이스 포인터를 관리 하기 위한 스마트 포인터 클래스입니다.|atlcomcli.h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|이 클래스는 COM 기반 메모리 루틴을 사용 하는 스마트 포인터 클래스의 기반을 제공 합니다.|atlcomcli.h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|COM 인터페이스 포인터를 관리 하기 위한 스마트 포인터 클래스입니다.|atlcomcli.h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|이 클래스는 COM 인터페이스 포인터의 컬렉션을 만들 때 유용한 메서드, 정적 함수 및 typedef를 제공 합니다.|atlcoll.h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|이 클래스는 구조체에 대 한 래퍼입니다 `SAFEARRAY Data Type` .|atlsafe.h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|이 클래스는 구조체에 대 한 래퍼입니다 `SAFEARRAYBOUND` .|atlsafe.h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|이 클래스는 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)클래스에 대 한 스레드 선택을 관리 합니다.|atlbase.h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|이 클래스는 변수의 값을 증가 및 감소 시키는 메서드를 제공 합니다.|atlbase.h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|이 클래스는 분리 인터페이스를 구현 합니다.|atlcom.h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|이 클래스는 `IUnknown` 포인터를 저장 하며 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 템플릿 클래스에 대 한 매개 변수로 사용 하도록 디자인 되었습니다.|atlcom.h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|이 클래스는 VARIANT 형식을 래핑하여 저장 된 데이터의 형식을 나타내는 멤버를 제공 합니다.|atlcomcli.h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|이 클래스는 다른 개체 내에 포함 된 창을 구현 합니다.|atlwin.h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|이 클래스는 CRT 메모리 루틴을 사용 하 여 메모리를 관리 하는 메서드를 제공 합니다.|atlcore.h|
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|이 클래스는 CRT 힙 함수를 사용 하 여 [Iatlmemmgr](../../atl/reference/iatlmemmgr-class.md) 을 구현 합니다.|atlmem.h|
|[CDacl](../../atl/reference/cdacl-class.md)|이 클래스는 DACL (임의 액세스 제어 목록) 구조체에 대 한 래퍼입니다.|atlsecurity.h|
|[CDebugReportHook 클래스](../../atl/reference/cdebugreporthook-class.md)|이 클래스를 사용 하 여 디버그 보고서를 명명 된 파이프로 보낼 수 있습니다.|atlutil.h|
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|이 클래스는 대문자와 소문자 사이에서 문자를 변환 하기 위한 두 개의 정적 함수를 제공 합니다.|atlcoll.h|
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|이 클래스는 기본 요소 비교 함수를 제공 합니다.|atlcoll.h|
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|이 클래스는 컬렉션 클래스에 대 한 기본 메서드 및 함수를 제공 합니다.|atlcoll.h|
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|이 클래스는 해시 값을 계산 하는 정적 함수를 제공 합니다.|atlcoll.h|
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|이 클래스는 모달 또는 모덜리스 대화 상자를 만드는 메서드를 제공 합니다.|atlwin.h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|이 클래스는 메시지 맵의 동적 체인을 지 원하는 메서드를 제공 합니다.|atlwin.h|
|[CElementTraits](../../atl/reference/celementtraits-class.md)|이 클래스는 컬렉션 클래스에서 이동, 복사, 비교 및 해시 작업을 위한 메서드와 함수를 제공 하는 데 사용 됩니다.|atlcoll.h|
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|이 클래스는 컬렉션 클래스에 대 한 기본 복사 및 이동 메서드를 제공 합니다.|atlcoll.h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|이 클래스는 컨테이너의 싱크에 컨트롤 속성 변경 내용에 대 한 알림을 제공 하는 메서드를 제공 합니다.|atlctl.h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|이 클래스는 Win32 전역 힙 함수를 사용 하 여 [Iatlmemmgr](../../atl/reference/iatlmemmgr-class.md) 을 구현 합니다.|atlmem.h|
|[CHandle](../../atl/reference/chandle-class.md)|이 클래스는 핸들 개체를 만들고 사용 하기 위한 메서드를 제공 합니다.|atlbase.h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|힙 포인터를 관리 하기 위한 스마트 포인터 클래스입니다.|atlcore.h|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|이 클래스는 여러 스마트 힙 포인터 클래스의 기본을 형성 합니다.|atlcore.h|
|[CHeapPtrElementTraits 클래스](../../atl/reference/cheapptrelementtraits-class.md)|이 클래스는 힙 포인터의 컬렉션을 만들 때 유용한 메서드, 정적 함수 및 typedef를 제공 합니다.|atlcoll.h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|이 클래스는 힙 포인터 목록을 생성할 때 유용한 메서드를 제공 합니다.|atlcoll.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|JPEG, GIF, BMP 및 PNG (이동식 네트워크 그래픽) 형식으로 이미지를 로드 하 고 저장 하는 기능을 포함 하 여 향상 된 비트맵 지원 기능을 제공 합니다.|atlimage.h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|이 클래스는 COM 인터페이스 포인터의 배열을 생성할 때 유용한 메서드를 제공 합니다.|atlcoll.h|
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|이 클래스는 COM 인터페이스 포인터 목록을 생성할 때 유용한 메서드를 제공 합니다.|atlcoll.h|
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|이 클래스는 Win32 로컬 힙 함수를 사용 하 여 [Iatlmemmgr](../../atl/reference/iatlmemmgr-class.md) 을 구현 합니다.|atlmem.h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|이 클래스를 사용 하면 다른 개체에서 개체의 메시지 맵을 액세스할 수 있습니다.|atlwin.h|
|[CNonStatelessWorker 클래스](../../atl/reference/cnonstatelessworker-class.md)|스레드 풀에서 요청을 수신 하 고 각 요청에서 만들어지고 소멸 된 작업자 개체에 전달 합니다.|atlutil.h|
|[Cno, Thread 클래스](../../atl/reference/cnoworkerthread-class.md)|`MonitorClass`동적 캐시 유지 관리를 사용 하지 않도록 설정 하려는 경우이 클래스를 템플릿 매개 변수 캐시 클래스의 인수로 사용 합니다.|atlutil.h|
|[CPathT 클래스](../../atl/reference/cpatht-class.md)|이 클래스는 경로를 나타냅니다.|atlpath.h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|이 클래스는 기본 데이터 형식으로 구성 된 컬렉션 클래스에 대 한 기본 메서드 및 함수를 제공 합니다.|atlcoll.h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|이 클래스는 private 개체 보안 설명자 개체를 나타냅니다.|atlsecurity.h|
|[CRBMap](../../atl/reference/crbmap-class.md)|이 클래스는 Red-Black 이진 트리를 사용 하 여 매핑 구조를 나타냅니다.|atlcoll.h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|이 클래스는 Red-Black 이진 트리를 사용 하 여 각 키를 둘 이상의 값에 연결할 수 있는 매핑 구조를 나타냅니다.|atlcoll.h|
|[CRBTree](../../atl/reference/crbtree-class.md)|이 클래스는 Red-Black 트리를 만들고 활용 하기 위한 메서드를 제공 합니다.|atlcoll.h|
|[CRegKey](../../atl/reference/cregkey-class.md)|이 클래스는 시스템 레지스트리에서 항목을 조작 하는 메서드를 제공 합니다.|atlbase.h|
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|이 클래스는 CRT 스레드에 대 한 생성 함수를 제공 합니다. 스레드에서 CRT 함수를 사용 하는 경우이 클래스를 사용 합니다.|atlbase.h|
|[CSacl](../../atl/reference/csacl-class.md)|이 클래스는 SACL (시스템 액세스 제어 목록) 구조체에 대 한 래퍼입니다.|atlsecurity.h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|이 클래스는 구조체에 대 한 씬 래퍼입니다 `SECURITY_ATTRIBUTES` .|atlsecurity.h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|이 클래스는 구조체에 대 한 래퍼입니다 `SECURITY_DESCRIPTOR` .|atlsecurity.h|
|[CSid](../../atl/reference/csid-class.md)|이 클래스는 `SID` (보안 식별자) 구조체에 대 한 래퍼입니다.|atlsecurity.h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|이 클래스는 간단한 배열을 관리 하기 위한 메서드를 제공 합니다.|atlsimpcoll.h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|이 클래스는 [CSimpleArray](../../atl/reference/csimplearray-class.md) 클래스에 대 한 도우미입니다.|atlsimpcoll.h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|이 클래스는 [CSimpleArray](../../atl/reference/csimplearray-class.md) 클래스에 대 한 도우미입니다.|atlsimpcoll.h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|이 클래스는 기본 모달 대화 상자를 구현 합니다.|atlwin.h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|이 클래스는 간단한 매핑 배열을 지원 합니다.|atlsimpcoll.h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|이 클래스는 [Csimplemap](../../atl/reference/csimplemap-class.md) 클래스에 대 한 도우미입니다.|atlsimpcoll.h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|이 클래스는 [Csimplemap](../../atl/reference/csimplemap-class.md) 클래스에 대 한 도우미입니다.|atlsimpcoll.h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|이 클래스는 스냅인 노드 개체를 구현 하는 메서드를 제공 합니다.|atlsnap.h|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|이 클래스는 스냅인 속성 페이지 개체를 구현 하는 메서드를 제공 합니다.|atlsnap.h|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|이 클래스는 스톡 속성 값을 지원 하기 위한 메서드를 제공 합니다.|atlctl.h|
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|이 클래스는 개체를 저장 하는 컬렉션 클래스에서 사용 하는 정적 함수를 제공 `CString` 합니다.|cstringt.h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|이 클래스는 컬렉션 클래스 개체에 저장 된 문자열과 관련 된 정적 함수를 제공 합니다. [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)와 유사 하지만 대/소문자를 구분 하지 않는 비교를 수행 합니다.|atlcoll.h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|이 클래스는 컬렉션 클래스 개체에 저장 된 문자열과 관련 된 정적 함수를 제공 합니다. 문자열 개체는를 참조로 처리 합니다.|atlcoll.h|
|[CThreadPool 클래스](../../atl/reference/cthreadpool-class.md)|이 클래스는 작업 항목의 큐를 처리 하는 작업자 스레드 풀을 제공 합니다.|atlutil.h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|이 클래스는 구조체에 대 한 래퍼입니다 `TOKEN_GROUPS` .|atlsecurity.h|
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|이 클래스는 구조체에 대 한 래퍼입니다 `TOKEN_PRIVILEGES` .|atlsecurity.h|
|[말아 클래스](../../atl/reference/curl-class.md)|이 클래스는 URL을 나타냅니다. 이를 통해 기존 URL 문자열을 구문 분석 하거나 처음부터 문자열을 작성 하 든 관계 없이 URL의 각 요소를 개별적으로 조작할 수 있습니다.|atlutil.h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|이 클래스는 문자열 변환 매크로 CT2AEX, CW2TEX, CW2CTEX 및 CT2CAEX와 typedef CW2A에서 사용 됩니다.|atlconv.h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|이 클래스는 문자열 변환 매크로 CW2CTEX 및 CT2CWEX 및 typedef CW2CW에 사용 됩니다.|atlconv.h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|이 클래스는 문자열 변환 매크로 CW2TEX 및 CT2WEX 및 typedef CW2W에 사용 됩니다.|atlconv.h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|이 클래스는 Win32 힙 할당 함수를 사용 하 여 [Iatlmemmgr](../../atl/reference/iatlmemmgr-class.md) 을 구현 합니다.|atlmem.h|
|[CWindow](../../atl/reference/cwindow-class.md)|이 클래스는 창을 조작 하는 메서드를 제공 합니다.|atlwin.h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|이 클래스는 창을 만들거나 서브클래싱 하는 메서드를 제공 합니다.|atlwin.h|
|[CWinTraits](../../atl/reference/cwintraits-class.md)|이 클래스는 창 개체를 만들 때 사용 되는 스타일을 표준화 하기 위한 메서드를 제공 합니다.|atlwin.h|
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|이 클래스는 창 개체를 만들 때 사용 되는 스타일을 표준화 하기 위한 메서드를 제공 합니다.|atlwin.h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|이 클래스는 창 클래스에 대 한 정보를 등록 하는 메서드를 제공 합니다.|atlwin.h|
|[CWorkerThread 클래스](../../atl/reference/cworkerthread-class.md)|이 클래스는 작업자 스레드를 만들거나 기존 작업자 스레드를 사용 하 고, 하나 이상의 커널 개체 핸들을 대기 하 고, 핸들 중 하나가 신호를 받으면 지정 된 클라이언트 함수를 실행 합니다.|atlutil.h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|이 클래스는 메서드에 대 한 인터페이스를 나타냅니다 `CreateInstance` .|atlbase.h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|이 클래스는 메모리 관리자에 대 한 인터페이스를 나타냅니다.|atlmem.h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|이 인터페이스는 호스트 된 컨트롤 또는 컨테이너의 특성을 지정 하는 메서드를 제공 합니다.|atlbase.h, ATLIFace.h|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|이 인터페이스는 호스트 된 컨트롤에 대 한 보완 앰비언트 속성을 구현 합니다.|atlbase.h, ATLIFace.h|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|이 인터페이스는 컨트롤과 해당 호스트 개체를 조작 하기 위한 메서드를 제공 합니다.|atlbase.h, ATLIFace.h|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|이 인터페이스는 사용이 허가 된 컨트롤과 해당 호스트 개체를 조작 하기 위한 메서드를 제공 합니다.|atlbase.h, ATLIFace.h|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|이 클래스는 컬렉션 클래스에서 사용 하는 메서드를 제공 합니다.|atlcom.h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|이 클래스는 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 개체의 컬렉션을 관리 하는 연결 지점 컨테이너를 구현 합니다.|atlcom.h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|이 클래스는 연결 지점을 구현 합니다.|atlcom.h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|이 클래스는 Uniform Data Transfer을 지원 하 고 연결을 관리 하기 위한 메서드를 제공 합니다.|atlctl.h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|이 클래스는 `IDispatch` 이중 인터페이스의 부분에 대 한 기본 구현을 제공 합니다.|atlcom.h|
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|이 클래스는 메서드의 구현을 제공 `IDispatch` 합니다.|atlcom.h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|이 클래스는 `IDispatch` 형식 라이브러리에서 형식 정보를 가져오지 않고 메서드의 구현을 제공 합니다.|atlcom.h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Microsoft HTML 구문 분석 및 렌더링 엔진에 대 한 인터페이스입니다.|atlbase.h, ATLIFace.h|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|이 클래스는 c + + 표준 라이브러리 컬렉션을 기반으로 하는 열거자 인터페이스를 정의 합니다.|atlcom.h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|이 클래스는 `IObjectSafety` 클라이언트에서 개체의 보안 수준을 검색 하 고 설정할 수 있도록 하는 인터페이스의 기본 구현을 제공 합니다.|atlctl.h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|이 클래스는 개체가 사이트와 통신할 수 있도록 하는 메서드를 제공 합니다.|atlcom.h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|이 클래스는 인터페이스의 기본 구현을 제공 `IOleControl` 하 고을 구현 `IUnknown` 합니다.|atlctl.h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|이 클래스는 내부 컨트롤과 해당 컨테이너 간의 통신을 지 원하는 메서드를 제공 합니다.|atlctl.h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|이 클래스는 `IUnknown` 창 없는 컨트롤에서 창 메시지를 받고 끌어서 놓기 작업에 참여할 수 있도록 하는 메서드를 구현 하 고 메서드를 제공 합니다.|atlctl.h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|이 클래스는를 구현 `IUnknown` 하며 컨테이너에서 컨트롤과 통신 하는 데 사용 되는 주 인터페이스입니다.|atlctl.h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|이 클래스는를 구현 `IUnknown` 하 고 클라이언트가 개체의 속성 페이지에 있는 정보에 액세스할 수 있도록 합니다.|atlctl.h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|이 클래스 `IUnknown` 는를 구현 하 고 개체에서 클라이언트 제공 속성 모음에 속성을 저장할 수 있도록 합니다.|atlcom.h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|이 클래스는 [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) 인터페이스를 구현 합니다.|atlcom.h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|이 클래스는 `IUnknown` 를 구현 하 고 [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) 인터페이스의 기본 구현을 제공 합니다.|atlcom.h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|이 클래스 `IUnknown` 는 및 [Ipointerinactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) 인터페이스 메서드를 구현 합니다.|atlctl.h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|이 클래스는 연결 가능한 개체의 나가는 인터페이스로 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) 인터페이스를 노출 합니다.|atlctl.h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|이 클래스 `IUnknown` 는 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)의 기본 구현을 구현 하 고 상속 합니다.|atlctl.h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|이 클래스는 `IUnknown` 를 구현 하 고 [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) 인터페이스의 기본 구현을 제공 합니다.|atlctl.h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|이 클래스는 [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) 및 [마샬러가 iprovideclassinfo2.getguid](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) 메서드의 기본 구현을 제공 합니다.|atlcom.h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|이 클래스는 컨테이너의 컨트롤 초기화를 단일 호출로 결합 합니다.|atlctl.h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|이 클래스는 `IUnknown` 를 구현 하 고 [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) 인터페이스의 기본 구현을 제공 합니다.|atlctl.h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|이 클래스는 인터페이스의 기본 구현을 제공 합니다 `IServiceProvider` .|atlcom.h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|이 클래스는 `IUnknown` 를 구현 하 고 [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) 인터페이스의 기본 구현을 제공 합니다.|atlcom.h|
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|이 클래스는 인터페이스의 기본 구현을 제공 `ISupportErrorInfo Interface` 하며 단일 인터페이스만 개체에서 오류를 생성 하는 경우에 사용할 수 있습니다.|atlcom.h|
|[IThreadPoolConfig 인터페이스](../../atl/reference/ithreadpoolconfig-interface.md)|이 인터페이스는 스레드 풀을 구성 하는 메서드를 제공 합니다.|atlutil.h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|이 클래스 `IUnknown` 는을 구현 하 고 [Iviewobject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)및 [iviewobjectex](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) 인터페이스의 기본 구현을 제공 합니다.|atlctl.h|
|[IWorkerThreadClient 인터페이스](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient` 는 [Cworkerthread](../../atl/reference/cworkerthread-class.md) 클래스의 클라이언트에서 구현 하는 인터페이스입니다.|atlutil.h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|이 클래스는 및에 대 한 래퍼를 제공 `CreateWindow` `CreateWindowEx` 합니다.|atlwin.h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|이 인수 어댑터 클래스를 사용 하면 포인터를 기준으로 구현 되는 `RECT` 함수에 포인터 또는 참조를 전달할 수 있습니다.|atlwin.h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|이 인수 어댑터 클래스를 사용 하면 호출자가 MAKEINTRESOURCE 매크로를 사용 하 여 ID를 문자열로 변환 하지 않고도 리소스 이름 (LPCTSTRs) 또는 리소스 Id (UINTs)를 함수에 전달할 수 있습니다.|atlwin.h|
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|이 클래스는 Windows 스레드에 대 한 생성 함수를 제공 합니다. 스레드에서 CRT 함수를 사용 하지 않는 경우이 클래스를 사용 합니다.|atlbase.h|

## <a name="see-also"></a>참고 항목

[ATL COM 데스크톱 구성 요소](../../atl/atl-com-desktop-components.md)<br/>
[함수](../../atl/reference/atl-functions.md)<br/>
[전역 변수](../../atl/reference/atl-global-variables.md)<br/>
[Typedefs](../../atl/reference/atl-typedefs.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
