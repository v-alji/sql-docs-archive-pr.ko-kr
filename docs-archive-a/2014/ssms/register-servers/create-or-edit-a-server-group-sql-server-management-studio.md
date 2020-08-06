---
title: 서버 그룹 만들기 또는 편집
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.editgroup.f1
- sql12.swb.newgroup.f1
helpviewer_keywords:
- Registered Servers [SQL Server], server groups
- server groups [SQL Server]
- groups [SQL Server], server
ms.assetid: d4a942bd-2dd1-42db-ad0e-e9a9ae5b856d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a8fbff8e52fdc91e2ed633ade725ecbb7baa5e9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737395"
---
# <a name="create-or-edit-a-server-group-sql-server-management-studio"></a><span data-ttu-id="952f2-102">서버 그룹 만들기 또는 편집(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="952f2-102">Create or Edit a Server Group (SQL Server Management Studio)</span></span>
  <span data-ttu-id="952f2-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 서버 그룹을 만들고 등록된 서버를 서버 그룹에 배치하여 등록된 서버에서 서버를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="952f2-103">This topic describes how to organize the servers in Registered Servers in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by creating server groups, and placing the servers in the server groups.</span></span> <span data-ttu-id="952f2-104">언제든지 등록된 서버에서 서버 그룹을 만들고, 또한 서버를 등록할 때 서버 그룹을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="952f2-104">You can create server groups in Registered Servers at any time, or you can create server groups when you register servers.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-create-a-server-group-in-registered-servers"></a><span data-ttu-id="952f2-105">등록된 서버에 서버 그룹을 만들려면</span><span class="sxs-lookup"><span data-stu-id="952f2-105">To create a server group in Registered Servers</span></span>  
  
1.  <span data-ttu-id="952f2-106">등록된 서버의 등록된 서버 도구 모음에서 해당 서버 유형을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="952f2-106">In Registered Servers, click the server type on the Registered Servers toolbar.</span></span> <span data-ttu-id="952f2-107">등록된 서버가 표시되지 않으면 **보기** 메뉴에서 **등록된 서버** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="952f2-107">If Registered Servers is not visible, click **Registered Servers** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="952f2-108">서버 또는 서버 그룹을 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **서버 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="952f2-108">Right-click a server or a server group, point to **New**, and then click **Server Group**.</span></span>  
  
3.  <span data-ttu-id="952f2-109">**새 서버 그룹** 대화 상자의 **그룹 이름** 목록 상자에 서버 그룹의 고유한 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="952f2-109">In the **New Server Group** dialog box, in the **Group name** list box, type a unique name for the server group.</span></span> <span data-ttu-id="952f2-110">서버 그룹 이름은 등록된 서버 트리의 현재 위치에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="952f2-110">The server group name must be unique for the current location in the Registered Servers tree.</span></span>  
  
4.  <span data-ttu-id="952f2-111">필요에 따라 **그룹 설명** 목록 상자에 서버 그룹을 설명하는 이름을 입력합니다(예: "라틴 아메리카 금융 서버").</span><span class="sxs-lookup"><span data-stu-id="952f2-111">In the **Group description** list box, optionally type a friendly name that describes the server group, for example, "Finance Servers for Latin America."</span></span>  
  
5.  <span data-ttu-id="952f2-112">**새 서버 그룹의 위치를 선택하세요.** 상자에서 그룹의 위치를 클릭한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="952f2-112">In the **Select a location for the new server group** box, click a location for the group, and then click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="952f2-113">이외에도 서버를 등록할 때 **새 그룹**을 클릭하고 **새 그룹** 대화 상자를 완료하면 새 서버 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="952f2-113">You can also create a new server group while you are registering a server by clicking **New Group**, and then completing the **New Group** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952f2-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="952f2-114">See Also</span></span>  
 [<span data-ttu-id="952f2-115">서버 등록</span><span class="sxs-lookup"><span data-stu-id="952f2-115">Register Servers</span></span>](register-servers.md)  
  
  
