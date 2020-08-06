---
title: 확장 저장 프로시저의 실행 특성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], executing
- executing extended stored procedures [SQL Server]
ms.assetid: 6fe1f7e8-cc02-49df-8a2a-d47a96ec3567
author: rothja
ms.author: jroth
ms.openlocfilehash: edbd73797699d65f694e91bc3035e0dc9366c9d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647020"
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a><span data-ttu-id="71a6c-102">확장 저장 프로시저의 실행 특징</span><span class="sxs-lookup"><span data-stu-id="71a6c-102">Execution Characteristics of Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="71a6c-103">대신 CLR 통합을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="71a6c-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="71a6c-104">확장 저장 프로시저 실행에는 다음과 같은 세 가지 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-104">The execution of an extended stored procedure has these characteristics:</span></span>  
  
-   <span data-ttu-id="71a6c-105">확장 저장 프로시저 함수는의 보안 컨텍스트에서 실행 됩니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="71a6c-105">The extended stored procedure function is executed under the security context of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="71a6c-106">확장 저장 프로시저 함수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스 공간에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-106">The extended stored procedure function runs in the process space of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="71a6c-107">확장 저장 프로시저 실행과 연결되는 스레드는 클라이언트 연결에 사용되는 스레드와 같은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-107">The thread associated with the execution of the extended stored procedure is the same one used for the client connection.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="71a6c-108">시스템 관리자는 확장 저장 프로시저를 서버에 추가하고 다른 사용자에게 실행 권한을 부여하기 전에 각 확장 저장 프로시저를 철저히 검토하여 유해 코드 또는 악성 코드가 포함되어 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-108">Before adding extended stored procedures to the server and granting execute permissions to other users, the system administrator should thoroughly review each extended stored procedure to make sure that it does not contain harmful or malicious code.</span></span>  
  
-  
  
 <span data-ttu-id="71a6c-109">확장 저장 프로시저 DLL을 로드 한 후에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는가 중지 되거나 관리자가 DBCC *DLL_name* (무료)를 사용 하 여 dll을 명시적으로 언로드할 때까지 dll이 서버의 주소 공간에 로드 된 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-109">After the extended stored procedure DLL is loaded, the DLL remains loaded in the address space of the server until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is stopped or the administrator explicitly unloads the DLL by using DBCC *DLL_name* (FREE).</span></span>  
  
 <span data-ttu-id="71a6c-110">[!INCLUDE[tsql](../../includes/tsql-md.md)]에서 EXECUTE 문을 사용하여 확장 저장 프로시저를 저장 프로시저처럼 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-110">The extended stored procedure can be executed from [!INCLUDE[tsql](../../includes/tsql-md.md)] as a stored procedure by using the EXECUTE statement:</span></span>  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a><span data-ttu-id="71a6c-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="71a6c-111">Parameters</span></span>  
 <span data-ttu-id="71a6c-112">\@ *retval*</span><span class="sxs-lookup"><span data-stu-id="71a6c-112">\@ *retval*</span></span>  
 <span data-ttu-id="71a6c-113">반환 값입니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-113">Is a return value.</span></span>  
  
 <span data-ttu-id="71a6c-114">\@*param1*</span><span class="sxs-lookup"><span data-stu-id="71a6c-114">\@ *param1*</span></span>  
 <span data-ttu-id="71a6c-115">입력 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-115">Is an input parameter.</span></span>  
  
 <span data-ttu-id="71a6c-116">\@*param2*</span><span class="sxs-lookup"><span data-stu-id="71a6c-116">\@ *param2*</span></span>  
 <span data-ttu-id="71a6c-117">입/출력 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-117">Is an input/output parameter.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="71a6c-118">확장 저장 프로시저는 성능 향상과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능 확장을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-118">Extended stored procedures offer performance enhancements and extend [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="71a6c-119">그러나 확장 저장 프로시저 DLL과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 같은 주소 공간을 공유하므로 문제가 있는 프로시저가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 작동에 부정적인 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-119">However, because the extended stored procedure DLL and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] share the same address space, a problem procedure can adversely affect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functioning.</span></span> <span data-ttu-id="71a6c-120">확장 저장 프로시저 DLL에서 throw하는 예외는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 처리되지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 영역에 손상을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-120">Although exceptions thrown by the extended stored procedure DLL are handled by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is possible to damage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data areas.</span></span> <span data-ttu-id="71a6c-121">보안 예방 조치로서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 관리자만 확장 저장 프로시저를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-121">As a security precaution, only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrators can add extended stored procedures to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="71a6c-122">이러한 프로시저는 설치하기 전에 철저히 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a6c-122">These procedures should be thoroughly tested before they are installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71a6c-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71a6c-123">See Also</span></span>  
 <span data-ttu-id="71a6c-124">[확장 저장 프로시저 프로그래밍](database-engine-extended-stored-procedures-programming.md) </span><span class="sxs-lookup"><span data-stu-id="71a6c-124">[Programming Extended Stored Procedures](database-engine-extended-stored-procedures-programming.md) </span></span>  
 [<span data-ttu-id="71a6c-125">SQL Server에 설치된 확장 저장 프로시저 쿼리</span><span class="sxs-lookup"><span data-stu-id="71a6c-125">Querying Extended Stored Procedures Installed in SQL Server</span></span>](querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  
