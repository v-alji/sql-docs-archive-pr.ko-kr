---
title: 로컬 CDC Service를 관리하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f9be649-cd93-40c1-bc48-0480106f207c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 437590d4b91f2fc80d5bb8a90251bf0dc7c8e18a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727312"
---
# <a name="how-to-manage-a-local-cdc-service"></a><span data-ttu-id="b927b-102">로컬 CDC Service를 관리하는 방법</span><span class="sxs-lookup"><span data-stu-id="b927b-102">How to Manage a Local CDC Service</span></span>
  <span data-ttu-id="b927b-103">이 절차에서는 CDC Service 구성 콘솔을 사용하여 특정 CDC Service를 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-103">This procedure describes how to use the CDC Service Configuration Console to manage specific CDC services.</span></span>  
  
### <a name="to-manage-a-specific-cdc-service"></a><span data-ttu-id="b927b-104">특정 CDC Service를 관리 하려면</span><span class="sxs-lookup"><span data-stu-id="b927b-104">To manage a specific CDC Service</span></span>  
  
1.  <span data-ttu-id="b927b-105">**시작** 메뉴에서 **Oracle CDC Service 구성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-105">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="b927b-106">CDC Service 구성 콘솔의 왼쪽 창에서 **로컬 CDC Service**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-106">From the left pane in the CDC Service Configuration Console, expand **Local CDC Services**.</span></span>  
  
3.  <span data-ttu-id="b927b-107">작업할 CDC Service를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-107">Select the CDC service you want to work with.</span></span>  
  
     <span data-ttu-id="b927b-108">작업할 CDC Service를 마우스 오른쪽 단추로 클릭하고 원하는 동작을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-108">You can also right-click the CDC service you want to work with and select the desired action.</span></span>  
  
     <span data-ttu-id="b927b-109">**OR**</span><span class="sxs-lookup"><span data-stu-id="b927b-109">**OR**</span></span>  
  
     <span data-ttu-id="b927b-110">CDC Service 구성 콘솔의 왼쪽 창에서 **로컬 CDC Service** 를 선택한 다음 CDC Service 구성 콘솔의 가운데 섹션에서 작업할 서비스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-110">Select **Local CDC Services** from the left pane in the CDC Service Configuration Console then select the service you want to work with from the middle section of the CDC Service Configuration Console.</span></span>  
  
     <span data-ttu-id="b927b-111">작업할 CDC Service를 마우스 오른쪽 단추로 클릭하고 원하는 동작을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-111">You can also right-click the CDC service you want to work with and select the desired action.</span></span>  
  
4.  <span data-ttu-id="b927b-112">CDC서비스를 작업할 때 다음과 같은 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-112">You can carry out the following tasks when working with a CDC service.</span></span>  
  
    -   <span data-ttu-id="b927b-113">**서비스 삭제**</span><span class="sxs-lookup"><span data-stu-id="b927b-113">**Delete the service**</span></span>  
  
         <span data-ttu-id="b927b-114">CDC Service 구성 콘솔 오른쪽의 **동작** 창에서 **삭제** 를 클릭하여 서비스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-114">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Delete** to delete the service.</span></span>  
  
         <span data-ttu-id="b927b-115">삭제할 CDC Service를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-115">You can also right-click the CDC service you want to delete and select **Delete**.</span></span>  
  
         <span data-ttu-id="b927b-116">**참고**: 서비스를 삭제할 때 서비스가 실행 중인 경우 서비스가 중지된 후에 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-116">**Note**: If the service is running when deleting the service, the service is stopped before being deleted.</span></span>  
  
         <span data-ttu-id="b927b-117">Oracle CDC Windows 서비스 정의를 삭제하려면 프로그램은 연결된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 MSXDBCDC 데이터베이스에 대한 액세스 권한을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-117">To delete an Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="b927b-118">**확인** 을 클릭하여 서비스를 삭제하면 프로그램은 MSXDBCDC 데이터베이스에서 Oracle CDC Service 등록을 삭제하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-118">When you click **OK** to delete the service, the program attempts to delete the Oracle CDC Service registration in the MSXDBCDC database.</span></span> <span data-ttu-id="b927b-119">권한 부족으로 인해 실패할 경우 사용자가 MSXDBCDC 데이터베이스의 업데이트 권한이 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력할 수 있는 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-119">If it fails due to lack of permissions, a dialog box is displayed to prompt the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
         <span data-ttu-id="b927b-120">SQL Server에 연결 대화 상자에 입력해야 하는 데이터에 대한 자세한 내용은 [Manage an Oracle CDC Service](manage-an-oracle-cdc-service.md) 및 [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b927b-120">For information about the data you must enter in the Connect to SQL Server dialog box, see [Manage an Oracle CDC Service](manage-an-oracle-cdc-service.md) and [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).</span></span>  
  
    -   <span data-ttu-id="b927b-121">**CDC Service 속성 편집**</span><span class="sxs-lookup"><span data-stu-id="b927b-121">**Edit the CDC Service Properties**</span></span>  
  
         <span data-ttu-id="b927b-122">CDC Service 구성 콘솔 오른쪽의 **동작** 창에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-122">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Properties**.</span></span>  
  
         <span data-ttu-id="b927b-123">속성을 편집할 CDC Service를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b927b-123">You can also right-click the CDC service where you want to edit the properties and select **Properties**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b927b-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b927b-124">See Also</span></span>  
 [<span data-ttu-id="b927b-125">Oracle CDC Service 관리</span><span class="sxs-lookup"><span data-stu-id="b927b-125">Manage an Oracle CDC Service</span></span>](manage-an-oracle-cdc-service.md)  
  
  
