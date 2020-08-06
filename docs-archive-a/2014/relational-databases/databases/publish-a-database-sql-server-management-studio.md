---
title: 데이터베이스 게시(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 98b2914e-7147-40af-ba7d-87253bbe8bf9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 652f2341d24c19e6c5ce34196b0e1c4dc5b09084
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650094"
---
# <a name="publish-a-database-sql-server-management-studio"></a><span data-ttu-id="eac8b-102">데이터베이스 게시(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="eac8b-102">Publish a Database (SQL Server Management Studio)</span></span>
  <span data-ttu-id="eac8b-103">**스크립트 생성 및 게시 마법사** 를 사용하여 전체 데이터베이스 또는 개별 데이터베이스 개체를 웹 호스팅 공급자에 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-103">You can use the **Generate and Publish Scripts Wizard** to publish an entire database or individual database objects to a Web hosting provider.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eac8b-104">이 항목에서 설명하는 기능은 데이터베이스 게시 마법사에서 제공했던 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-104">The functionality described in this topic used to be provided by the Publish Database Wizard.</span></span> <span data-ttu-id="eac8b-105">게시 기능이 스크립트 생성 및 게시 마법사에 추가되었고 데이터베이스 게시 마법사는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-105">The publishing functionality has been added to the Generate and Publish Scripts Wizard, and the Publish Database Wizard has been discontinued.</span></span>  
  
## <a name="generate-and-publish-scripts-wizard"></a><span data-ttu-id="eac8b-106">스크립트 생성 및 게시 마법사</span><span class="sxs-lookup"><span data-stu-id="eac8b-106">Generate and Publish Scripts Wizard</span></span>  
 <span data-ttu-id="eac8b-107">스크립트 생성 및 게시 마법사를 사용하여 데이터베이스 또는 선택된 데이터베이스 개체를 웹 호스팅 공급자에 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-107">The Generate and Publish Scripts Wizard can be used to publish a database or selected database objects to a Web hosting provider.</span></span> <span data-ttu-id="eac8b-108">SQL Server 웹 호스팅 공급자는 웹 서비스에 대한 연결 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-108">A SQL Server Web hosting provider is a connectivity interface to a Web service.</span></span> <span data-ttu-id="eac8b-109">웹 서비스는 CodePlex의 SQL Server Hosting Toolkit에 있는 데이터베이스 게시 서비스 프로젝트를 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-109">The Web service is created by using the Database Publishing Services project from the SQL Server Hosting Toolkit on CodePlex.</span></span> <span data-ttu-id="eac8b-110">웹 서비스를 통해 웹 호스터 고객은 스크립트 생성 및 게시 마법사를 사용하여 데이터베이스를 서비스로 쉽게 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-110">The Web service makes it easy for the Web hoster customers to publish their databases to the service by using the Generate and Publish Scripts Wizard.</span></span> <span data-ttu-id="eac8b-111">SQL Server Hosting Toolkit을 다운로드하는 방법은 [SQL Server 데이터 게시 서비스(SQL Server Database Publishing Services)](https://go.microsoft.com/fwlink/?LinkId=142025)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eac8b-111">For more information about downloading the SQL Server Hosting Toolkit, see [SQL Server Database Publishing Services](https://go.microsoft.com/fwlink/?LinkId=142025).</span></span>  
  
 <span data-ttu-id="eac8b-112">스크립트 생성 및 게시 마법사는 데이터베이스를 전송하기 위한 스크립트를 만드는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-112">The Generate and Publish Scripts Wizard can also be used to create a script for transferring a database.</span></span>  
  
#### <a name="to-publish-a-database-to-a-web-service"></a><span data-ttu-id="eac8b-113">웹 서비스에 데이터베이스를 게시하려면</span><span class="sxs-lookup"><span data-stu-id="eac8b-113">To publish a database to a Web service</span></span>  
  
1.  <span data-ttu-id="eac8b-114">개체 탐색기에서 **데이터베이스**를 확장하고 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음, **태스크**를 가리키고 **스크립트 생성 및 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-114">In Object Explorer, expand **Databases**, right-click a database, point to **Tasks**, and then click **Generate and Publish Scripts**.</span></span> <span data-ttu-id="eac8b-115">마법사의 단계에 따라 게시할 데이터베이스 개체를 스크립팅합니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-115">Follow the steps in the wizard to script the database objects for publishing.</span></span>  
  
2.  <span data-ttu-id="eac8b-116">**개체 선택** 페이지에서 웹 호스팅 서비스에 게시할 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-116">On the **Choose Objects** page, select the objects to be published to the Web hosting service.</span></span>  
  
3.  <span data-ttu-id="eac8b-117">**스크립팅 옵션 설정** 페이지에서 **웹 서비스에 게시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-117">On the **Set Scripting Options** page, select **Publish to Web Service**.</span></span>  
  
    1.  <span data-ttu-id="eac8b-118">**공급자** 상자에서 웹 서비스의 공급자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-118">In the **Provider** box, specify the provider for your Web service.</span></span> <span data-ttu-id="eac8b-119">웹 호스팅 공급자를 구성하지 않은 경우 **공급자 관리** 를 선택하고 **공급자 관리** 대화 상자를 사용하여 웹 서비스의 공급자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-119">If you have not configured a Web hosting provider, select **Manage Providers** and use the **Manage Providers** dialog box to configure a provider for your Web service.</span></span>  
  
    2.  <span data-ttu-id="eac8b-120">고급 게시 옵션을 지정하려면 **웹 서비스에 게시** 섹션에서 **고급** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-120">To specify advanced publishing options, select the **Advanced** button in the **Publish to Web Service** section.</span></span>  
  
4.  <span data-ttu-id="eac8b-121">**요약** 페이지에서 선택 항목을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-121">On the **Summary** page, review your selections.</span></span> <span data-ttu-id="eac8b-122">선택 항목을 변경하려면 **이전** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-122">Click **Previous** to change your selections.</span></span> <span data-ttu-id="eac8b-123">선택한 개체를 게시하려면 **다음** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-123">Click **Next** to publish the objects you selected.</span></span>  
  
5.  <span data-ttu-id="eac8b-124">**스크립트 저장 또는 게시** 페이지에서 게시 진행률을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="eac8b-124">On the **Save or Publish Scripts** page, monitor the progress of the publication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eac8b-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eac8b-125">See Also</span></span>  
 <span data-ttu-id="eac8b-126">[스크립트 생성&#40;SQL Server Management Studio&#41;](../scripting/generate-scripts-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="eac8b-126">[Generate Scripts &#40;SQL Server Management Studio&#41;](../scripting/generate-scripts-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="eac8b-127">데이터베이스를 다른 서버로 복사</span><span class="sxs-lookup"><span data-stu-id="eac8b-127">Copy Databases to Other Servers</span></span>](copy-databases-to-other-servers.md)  
  
  
