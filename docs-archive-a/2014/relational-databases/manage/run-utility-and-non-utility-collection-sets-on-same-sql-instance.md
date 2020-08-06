---
title: SQL Server 같은 인스턴스에서 유틸리티 및 유틸리티 이외의 컬렉션 집합을 실행 하는 경우의 고려 사항 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67df2d65cc9da4026377e77c152c0d78f3749932
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652108"
---
# <a name="considerations-for-running-utility-and-non-utility-collection-sets-on-the-same-instance-of-sql-server"></a><span data-ttu-id="3c14f-102">같은 SQL Server 인스턴스에서 유틸리티 및 유틸리티 이외의 컬렉션 집합을 실행하기 위한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3c14f-102">Considerations for Running Utility and non-Utility Collection Sets on the Same Instance of SQL Server</span></span>
  <span data-ttu-id="3c14f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 컬렉션 집합을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 이외의 컬렉션 집합과 함께 사용하는 것이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14f-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection set is supported side-by-side with non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets.</span></span> <span data-ttu-id="3c14f-104">즉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티의 멤버이면 다른 컬렉션 집합으로 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14f-104">That is, a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be monitored by other collection sets while it is a member of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="3c14f-105">그러나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에 등록하는 동안에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 이외의 데이터 컬렉션 기능을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14f-105">However, you must disable non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility data collection functionality while the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is being enrolled into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
 <span data-ttu-id="3c14f-106">UCP를 인스턴스에 등록한 후에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 이외의 컬렉션 집합을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14f-106">After the instance is enrolled with the UCP, you can restart non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets.</span></span> <span data-ttu-id="3c14f-107">그러나 관리되는 인스턴스의 모든 컬렉션 집합은 해당 데이터를 UMDW(유틸리티 관리 데이터 웨어하우스)로 업로드합니다. UMDW의 파일 이름은 sysutility_mdw입니다.</span><span class="sxs-lookup"><span data-stu-id="3c14f-107">Note, however, that all collection sets on the managed instance will upload their data to the utility management data warehouse (UMDW); the UMDW file name is sysutility_mdw.</span></span>  
  
 <span data-ttu-id="3c14f-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 컬렉션 집합을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 이외의 컬렉션 집합과 함께 실행하려면 다음 사항을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="3c14f-108">To run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets side-by-side with non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility collection sets, consider the following points:</span></span>  
  
-   <span data-ttu-id="3c14f-109">컬렉션 집합을 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14f-109">Side-by-side collection sets are supported.</span></span>  
  
-   <span data-ttu-id="3c14f-110">인스턴스를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에 등록하는 동안에는 기존 데이터 수집기를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14f-110">You must disable existing data collectors while enrolling instances into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
-   <span data-ttu-id="3c14f-111">유효성 검사 요구 사항을 통과하려면 UCP를 만들기 전에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서, 그리고 이를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에 등록하기 전에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 다음 저장 프로시저를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14f-111">To pass validation requirements, you must run the following stored procedures on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you create a UCP, and on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you enroll it into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility:</span></span>  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     <span data-ttu-id="3c14f-112">UCP 만들기 마법사나 관리되는 인스턴스 추가 마법사를 시작하기 전에 이러한 저장 프로시저를 실행하지 않으면 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14f-112">If you do not run these stored procedures before you launch the Create UCP Wizard or Add Managed Instance Wizard, the operation will fail.</span></span>  
  
-   <span data-ttu-id="3c14f-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스에서 모든 컬렉션 집합에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]유틸리티 UMDW(sysutility_mdw)를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14f-113">You must use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility UMDW (sysutility_mdw) for all collection sets on a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c14f-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c14f-114">See Also</span></span>  
 <span data-ttu-id="3c14f-115">[SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="3c14f-115">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="3c14f-116">유틸리티 제어 지점 데이터 웨어하우스 구성&#40;SQL Server 유틸리티&#41;</span><span class="sxs-lookup"><span data-stu-id="3c14f-116">Configure Your Utility Control Point Data Warehouse &#40;SQL Server Utility&#41;</span></span>](configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  
