---
title: 중앙 관리 서버를 사용하여 여러 서버 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- central management server
- multiserver administration [SQL Server]
- master servers [SQL Server], central management servers
- target configuration [SQL Server]
- server configuration [SQL Server]
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3906165b595f6faa15812f70377a3bc0f550e52e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731767"
---
# <a name="administer-multiple-servers-using-central-management-servers"></a><span data-ttu-id="13017-102">중앙 관리 서버를 사용하여 여러 서버 관리</span><span class="sxs-lookup"><span data-stu-id="13017-102">Administer Multiple Servers Using Central Management Servers</span></span>
  <span data-ttu-id="13017-103">중앙 관리 서버를 지정하고 서버 그룹을 만들어 여러 서버를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13017-103">You can administer multiple servers by designating Central Management Servers and creating server groups.</span></span>  
  
## <a name="benefits-of-central-management-servers-and-server-groups"></a><span data-ttu-id="13017-104">중앙 관리 서버 및 서버 그룹의 이점</span><span class="sxs-lookup"><span data-stu-id="13017-104">Benefits of Central Management Servers and Server Groups</span></span>  
 <span data-ttu-id="13017-105">중앙 관리 서버로 지정된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스는 하나 이상의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 대한 연결 정보를 포함하는 서버 그룹을 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="13017-105">An instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is designated as a Central Management Server maintains server groups that contain the connection information for one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="13017-106">서버 그룹에 대해 [!INCLUDE[tsql](../includes/tsql-md.md)] 문과 정책 기반 관리 정책을 동시에 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13017-106">[!INCLUDE[tsql](../includes/tsql-md.md)] statements and Policy-Based Management policies can be executed at the same time against server groups.</span></span> <span data-ttu-id="13017-107">중앙 관리 서버를 통해 관리되는 인스턴스에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로그 파일을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13017-107">You can also view the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] log files on instances that are managed through a Central Management Server.</span></span> <span data-ttu-id="13017-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 이전의 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 버전은 중앙 관리 서버로 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13017-108">Versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] cannot be designated as a Central Management Server.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="13017-109">문을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13017-109">statements can also be executed against local server groups in Registered Servers.</span></span>  
  
### <a name="related-tasks"></a><span data-ttu-id="13017-110">관련 작업</span><span class="sxs-lookup"><span data-stu-id="13017-110">Related Tasks</span></span>  
 <span data-ttu-id="13017-111">중앙 관리 서버 및 서버 그룹을 만들려면 **의** 등록된 서버 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]창을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="13017-111">To create a Central Management Server and server groups, use the **Registered Servers** window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="13017-112">중앙 관리 서버는 자신이 유지 관리하는 그룹의 멤버가 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13017-112">Note that the Central Management Server cannot be a member of a group that it maintains.</span></span> <span data-ttu-id="13017-113">중앙 관리 서버 및 서버 그룹을 만드는 방법은 [중앙 관리 서버 및 서버 그룹 만들기&#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13017-113">For more information about how to create Central Management Servers and server groups, see [Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13017-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13017-114">See Also</span></span>  
 [<span data-ttu-id="13017-115">정책 기반 관리를 사용하여 서버 관리</span><span class="sxs-lookup"><span data-stu-id="13017-115">Administer Servers by Using Policy-Based Management</span></span>](policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
