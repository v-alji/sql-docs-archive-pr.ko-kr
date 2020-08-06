---
title: 확장 저장 프로시저 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- warnings [SQL Server]
- extended stored procedures [SQL Server], debugging
- extended stored procedures [SQL Server], creating
- messages [SQL Server], extended stored procedures
ms.assetid: 9f7c0cdb-6d88-44c0-b049-29953ae75717
author: rothja
ms.author: jroth
ms.openlocfilehash: d243b27b8542ec5fe10d795de1729d6c1fe484c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653392"
---
# <a name="creating-extended-stored-procedures"></a><span data-ttu-id="1d6e0-102">확장 저장 프로시저 만들기</span><span class="sxs-lookup"><span data-stu-id="1d6e0-102">Creating Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="1d6e0-103">대신 CLR 통합을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="1d6e0-104">확장 저장 프로시저는 프로토타입이 다음과 같은 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-104">An extended stored procedure is a function with a prototype:</span></span>  
  
 <span data-ttu-id="1d6e0-105">SRVRETCODE *xp_extendedProcName* **(** SRVPROC **\*);**</span><span class="sxs-lookup"><span data-stu-id="1d6e0-105">SRVRETCODE *xp_extendedProcName* **(** SRVPROC **\*);**</span></span>  
  
 <span data-ttu-id="1d6e0-106">접두사 xp_는 필요에 따라 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-106">Using the prefix xp_ is optional.</span></span> <span data-ttu-id="1d6e0-107">확장 저장 프로시저의 이름은 서버에 설치된 코드 페이지/정렬 순서에 관계없이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 참조할 때는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-107">Extended stored procedure names are case sensitive when referenced in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, regardless of code page/sort order installed on the server.</span></span> <span data-ttu-id="1d6e0-108">DLL을 빌드하는 경우 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-108">When you build a DLL:</span></span>  
  
-   <span data-ttu-id="1d6e0-109">진입점이 필요하면 DllMain 함수를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-109">If an entry point is necessary, write a DllMain function.</span></span>  
  
     <span data-ttu-id="1d6e0-110">이 함수는 옵션입니다. 원본 코드에서 이 함수를 제공하지 않으면 컴파일러가 자체 버전에 연결하며 이 경우 아무 작업도 수행되지 않고 TRUE가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-110">This function is optional; if you do not provide it in source code, the compiler links its own version, which does nothing but return TRUE.</span></span> <span data-ttu-id="1d6e0-111">DllMain 함수를 제공하면 스레드나 프로세스가 DLL에 연결되거나 DLL에서 분리될 때 운영 체제에서 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-111">If you provide a DllMain function, the operating system calls this function when a thread or process attaches to or detaches from the DLL.</span></span>  
  
-   <span data-ttu-id="1d6e0-112">DLL 외부에서 호출된 모든 함수(모든 확장 저장 프로시저 Efunction)는 내보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-112">All functions called from outside the DLL (all extended stored procedure Efunctions) must be exported.</span></span>  
  
     <span data-ttu-id="1d6e0-113">.Def 파일의 EXPORTS 섹션에서 이름을 나열 하 여 함수를 내보내거나, Microsoft 컴파일러 확장인 __declspec (dllexport)를 사용 하 여 소스 코드의 함수 이름에 접두사를 지정할 수 있습니다 ( \_ _declspec ()는 두 개의 밑줄로 시작 됨).</span><span class="sxs-lookup"><span data-stu-id="1d6e0-113">You can export a function by listing its name in the EXPORTS section of a .def file, or you can prefix the function name in the source code with __declspec(dllexport), a Microsoft compiler extension (Note that \__declspec() begins with two underscores).</span></span>  
  
 <span data-ttu-id="1d6e0-114">확장 저장 프로시저 DLL을 만드는 데 필요한 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-114">These files are required for creating an extended stored procedure DLL.</span></span>  
  
|<span data-ttu-id="1d6e0-115">파일</span><span class="sxs-lookup"><span data-stu-id="1d6e0-115">File</span></span>|<span data-ttu-id="1d6e0-116">Description</span><span class="sxs-lookup"><span data-stu-id="1d6e0-116">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1d6e0-117">Srv.h</span><span class="sxs-lookup"><span data-stu-id="1d6e0-117">Srv.h</span></span>|<span data-ttu-id="1d6e0-118">확장 저장 프로시저 API 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="1d6e0-118">Extended Stored Procedure API header file</span></span>|  
|<span data-ttu-id="1d6e0-119">Opends60.lib</span><span class="sxs-lookup"><span data-stu-id="1d6e0-119">Opends60.lib</span></span>|<span data-ttu-id="1d6e0-120">Opends60.dll용 가져오기 라이브러리</span><span class="sxs-lookup"><span data-stu-id="1d6e0-120">Import library for Opends60.dll</span></span>|  
  
 <span data-ttu-id="1d6e0-121">확장 저장 프로시저 DLL을 만들려면 동적 연결 라이브러리 형식의 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-121">To create an extended stored procedure DLL, create a project of type Dynamic Link Library.</span></span> <span data-ttu-id="1d6e0-122">DLL을 만드는 방법은 개발 환경 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-122">For more information about creating a DLL, see the development environment documentation.</span></span>  
  
 <span data-ttu-id="1d6e0-123">모든 확장 저장 프로시저 DLL에서 다음 함수를 구현하고 내보내는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-123">It is highly recommended that all extended stored procedure DLLs implement and export the following function:</span></span>  
  
```  
__declspec(dllexport) ULONG __GetXpVersion()  
{  
   return ODS_VERSION;  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="1d6e0-124">__declspec(dllexport)은 Microsoft 전용 컴파일러 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-124">__declspec(dllexport) is a Microsoft-specific compiler extension.</span></span> <span data-ttu-id="1d6e0-125">컴파일러에서 이 지시어를 지원하지 않으면 DEF 파일의 EXPORTS 섹션 아래에서 이 함수를 내보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-125">If your compiler does not support this directive, you should export this function in your DEF file under the EXPORTS section.</span></span>  
  
 <span data-ttu-id="1d6e0-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]이 T260 추적 플래그를 사용 하 여 시작 되거나 시스템 관리자 권한이 있는 사용자가 DBCC TRACEON (260)를 실행 하 고 확장 저장 프로시저 dll이 __GetXpVersion ()를 지원 하지 않는 경우 경고 메시지 (오류 8131: 확장 저장 프로시저 dll '% '이 (가) _GetXpVersion 내보내기 안 함 \_ ()이 오류 로그에 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started with the trace flag -T260 or if a user with system administrator privileges runs DBCC TRACEON (260), and if the extended stored procedure DLL does not support __GetXpVersion(), a warning message (Error 8131: Extended stored procedure DLL '%' does not export \__GetXpVersion().) is printed to the error log.</span></span> <span data-ttu-id="1d6e0-127">\__GetXpVersion ()는 두 개의 밑줄로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-127">(Note that \__GetXpVersion() begins with two underscores.)</span></span>  
  
 <span data-ttu-id="1d6e0-128">확장 저장 프로시저 DLL이 __GetXpVersion()을 내보내지만 함수에서 반환하는 버전이 서버에 필요한 버전보다 낮을 경우 함수에서 반환한 버전과 서버에 필요한 버전을 알리는 경고 메시지가 오류 로그에 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-128">If the extended stored procedure DLL exports __GetXpVersion(), but the version returned by the function is less than that required by the server, a warning message stating the version returned by the function and the version expected by the server is printed to the error log.</span></span> <span data-ttu-id="1d6e0-129">이 메시지가 표시 되 면 _GetXpVersion ()에서 잘못 된 값을 반환 \_ 하거나 이전 버전의 srv를 사용 하 여 컴파일하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-129">If you get this message, you are returning an incorrect value from \__GetXpVersion(), or you are compiling with an older version of srv.h.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d6e0-130">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 함수인 SetErrorMode는 확장 저장 프로시저 내에서 호출하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-130">SetErrorMode, a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 function, should not be called in extended stored procedures.</span></span>  
  
 <span data-ttu-id="1d6e0-131">장기 실행 확장 저장 프로시저의 경우 연결이 끊기거나 일괄 처리가 중단될 경우 프로시저가 자동으로 종료될 수 있도록 주기적으로 srv_got_attention을 호출하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-131">It is recommended that a long-running extended stored procedure should call srv_got_attention periodically so that the procedure can terminate itself if the connection is killed or the batch is aborted.</span></span>  
  
 <span data-ttu-id="1d6e0-132">확장 저장 프로시저 DLL을 디버깅하려면 DLL을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn 디렉터리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-132">To debug an extended stored procedure DLL, copy it to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn directory.</span></span> <span data-ttu-id="1d6e0-133">디버깅 세션에 사용할 실행 파일을 지정 하려면 실행 파일의 경로와 파일 이름을 입력 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (예: C:\PROGRAM Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe).</span><span class="sxs-lookup"><span data-stu-id="1d6e0-133">To specify the executable for the debugging session, enter the path and file name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executable file (for example, C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe).</span></span> <span data-ttu-id="1d6e0-134">Sqlservr.exe 인수에 대 한 자세한 내용은 [Sqlservr.exe 응용 프로그램](../../tools/sqlservr-application.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d6e0-134">For information about sqlservr arguments, see [sqlservr Application](../../tools/sqlservr-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d6e0-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d6e0-135">See Also</span></span>  
 [<span data-ttu-id="1d6e0-136">srv_got_attention &#40;확장 저장 프로시저 API&#41;</span><span class="sxs-lookup"><span data-stu-id="1d6e0-136">srv_got_attention &#40;Extended Stored Procedure API&#41;</span></span>](../extended-stored-procedures-reference/srv-got-attention-extended-stored-procedure-api.md)  
  
  
