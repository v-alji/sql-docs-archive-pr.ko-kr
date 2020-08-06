---
title: 연결에 대 한 가장 및 자격 증명 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
author: rothja
ms.author: jroth
ms.openlocfilehash: cdbc52e07f4502adda7301ce7f635c050ed9c3c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652159"
---
# <a name="impersonation-and-credentials-for-connections"></a><span data-ttu-id="952e7-102">연결에 대한 가장 및 자격 증명</span><span class="sxs-lookup"><span data-stu-id="952e7-102">Impersonation and Credentials for Connections</span></span>
  <span data-ttu-id="952e7-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR(공용 언어 런타임) 통합에서 Windows 인증 사용은 복잡하지만 SQL Server 인증을 사용하는 것보다 더 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-103">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] common language runtime (CLR) integration, using Windows Authentication is complex, but is more secure than using SQL Server Authentication.</span></span> <span data-ttu-id="952e7-104">Windows 인증을 사용하는 경우 다음 사항을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="952e7-104">When using Windows Authentication, keep in mind the following considerations.</span></span>  
  
 <span data-ttu-id="952e7-105">기본적으로 Windows에 연결하는 SQL Server 프로세스는 SQL Server Windows 서비스 계정의 보안 컨텍스트를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-105">By default, a SQL Server process that connects out to Windows acquires the security context of the SQL Server Windows service account.</span></span> <span data-ttu-id="952e7-106">그러나 CLR 함수를 프록시 ID에 매핑하여 해당 아웃바운드 연결이 Windows 서비스 계정과는 다른 보안 컨텍스트를 사용하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-106">But it is possible to map a CLR function to a proxy identity, so that its outbound connections have a different security context than that of the Windows service account.</span></span>  
  
 <span data-ttu-id="952e7-107">경우에 따라 서비스 계정으로 실행하는 대신 `SqlContext.WindowsIdentity` 속성을 사용하여 호출자를 가장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-107">In some cases, you may want to impersonate the caller by using the `SqlContext.WindowsIdentity` property instead of running as the service account.</span></span> <span data-ttu-id="952e7-108">`WindowsIdentity` 인스턴스는 호출 코드를 호출한 클라이언트의 ID를 나타내며, 클라이언트에서 Windows 인증을 사용한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-108">The `WindowsIdentity` instance represents the identity of the client that invoked the calling code, and is only available when the client used Windows Authentication.</span></span> <span data-ttu-id="952e7-109">`WindowsIdentity` 인스턴스를 얻은 후 `Impersonate`를 호출하여 스레드의 보안 토큰을 변경한 다음 클라이언트 대신 ADO.NET 연결을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-109">After you have obtained the `WindowsIdentity` instance, you can call `Impersonate` to change the security token of the thread, and then open ADO.NET connections on behalf of the client.</span></span>  
  
 <span data-ttu-id="952e7-110">SQLContext를 호출한 후에는 로컬 데이터에 액세스할 수 없으며 시스템 데이터에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-110">After you call SQLContext.WindowsIdentity.Impersonate, you cannot access local data and you cannot access system data.</span></span> <span data-ttu-id="952e7-111">데이터에 다시 액세스 하려면 WindowsImpersonationContext를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-111">To access data again, you have to call WindowsImpersonationContext.Undo.</span></span>  
  
 <span data-ttu-id="952e7-112">다음 예에서는 `SqlContext.WindowsIdentity` 속성을 사용하여 호출자를 가장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-112">The following example shows how to impersonate the caller by using the `SqlContext.WindowsIdentity` property.</span></span>  
  
 <span data-ttu-id="952e7-113">Visual C#</span><span class="sxs-lookup"><span data-stu-id="952e7-113">Visual C#</span></span>  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="952e7-114">가장의 동작 변경에 대 한 자세한 내용은 [2014 SQL Server 데이터베이스 엔진 기능에 대 한 주요 변경 내용](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="952e7-114">For information about behavior changes in impersonation, see [Breaking Changes to Database Engine Features in SQL Server 2014](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="952e7-115">또한 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows ID 값을 받은 경우 기본적으로 해당 인스턴스를 다른 컴퓨터에 전파할 수 없습니다. Windows 보안 인프라에서 기본적으로 이 작업이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-115">Furthermore, if you obtained the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows identity instance, by default you cannot propagate that instance to another computer; Windows security infrastructure restricts that by default.</span></span> <span data-ttu-id="952e7-116">하지만 신뢰할 수 있는 여러 컴퓨터에 Windows ID를 전파할 수 있는 "위임"이라는 메커니즘이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-116">There is, however, a mechanism called "delegation" that enables propagation of Windows identities across multiple trusted computers.</span></span> <span data-ttu-id="952e7-117">"[Kerberos 프로토콜 전환 및 제한 된 위임](https://go.microsoft.com/fwlink/?LinkId=50419)" TechNet 문서에서 위임에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="952e7-117">You can learn more about delegation in the TechNet article, "[Kerberos Protocol Transition and Constrained Delegation](https://go.microsoft.com/fwlink/?LinkId=50419)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952e7-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="952e7-118">See Also</span></span>  
 [<span data-ttu-id="952e7-119">SqlContext 개체</span><span class="sxs-lookup"><span data-stu-id="952e7-119">SqlContext Object</span></span>](../../clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
