---
title: 패키지 업그레이드 (SSIS 패키지 업그레이드 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.upgradingpackage.f1
ms.assetid: cdb842e3-2e59-4ede-b127-be4fde46875c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d13228dabc1566b592733da4afd8ebde3671ee0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647736"
---
# <a name="upgrading-the-packages-ssis-package-upgrade-wizard"></a><span data-ttu-id="b11dd-102">패키지 업그레이드(SSIS 패키지 업그레이드 마법사)</span><span class="sxs-lookup"><span data-stu-id="b11dd-102">Upgrading the Packages (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="b11dd-103">**패키지 업그레이드** 페이지를 사용하여 패키지 업그레이드의 진행률을 보고 업그레이드 프로세스를 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-103">Use the **Upgrading the Packages** page to view the progress of package upgrade and to interrupt the upgrade process.</span></span> <span data-ttu-id="b11dd-104">[!INCLUDE[ssIS](../includes/ssis-md.md)] 패키지 업그레이드 마법사는 선택된 패키지를 하나씩 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-104">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard upgrades the selected packages one by one.</span></span>  
  
 <span data-ttu-id="b11dd-105">**SQL Server 데이터베이스 또는 패키지 저장소에 저장된 업그레이드된 패키지를 보려면**</span><span class="sxs-lookup"><span data-stu-id="b11dd-105">**To view upgraded packages that were saved to a SQL Server database or to the package store**</span></span>  
  
-   <span data-ttu-id="b11dd-106">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]의 개체 탐색기에서 로컬 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]인스턴스에 연결한 다음 **저장된 패키지** 노드를 확장하여 업그레이드된 패키지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-106">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], in Object Explorer, connect to the local instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], and then expand the **Stored Packages** node to see the packages that were upgraded.</span></span>  
  
 <span data-ttu-id="b11dd-107">**SQL Server Data Tools에서 업그레이드된 패키지를 보려면**</span><span class="sxs-lookup"><span data-stu-id="b11dd-107">**To view upgraded packages that were upgraded from SQL Server Data Tools**</span></span>  
  
-   <span data-ttu-id="b11dd-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 연 다음 **SSIS 패키지** 노드를 확장하여 업그레이드된 패키지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and then expand the **SSIS Packages** node to see the upgraded packages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b11dd-109">옵션</span><span class="sxs-lookup"><span data-stu-id="b11dd-109">Options</span></span>  
 <span data-ttu-id="b11dd-110">**메시지 창**</span><span class="sxs-lookup"><span data-stu-id="b11dd-110">**Message pane**</span></span>  
 <span data-ttu-id="b11dd-111">업그레이드 프로세스 중 진행 메시지 및 요약 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-111">Displays progress messages and summary information during the upgrade process.</span></span>  
  
 <span data-ttu-id="b11dd-112">**동작**</span><span class="sxs-lookup"><span data-stu-id="b11dd-112">**Action**</span></span>  
 <span data-ttu-id="b11dd-113">업그레이드 동작을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-113">View the actions in the upgrade.</span></span>  
  
 <span data-ttu-id="b11dd-114">**상태**</span><span class="sxs-lookup"><span data-stu-id="b11dd-114">**Status**</span></span>  
 <span data-ttu-id="b11dd-115">각 동작의 결과를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-115">View the result of each action.</span></span>  
  
 <span data-ttu-id="b11dd-116">**Message**</span><span class="sxs-lookup"><span data-stu-id="b11dd-116">**Message**</span></span>  
 <span data-ttu-id="b11dd-117">각 동작에서 생성된 오류 메시지를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-117">View the error messages that each action generates.</span></span>  
  
 <span data-ttu-id="b11dd-118">**중지**</span><span class="sxs-lookup"><span data-stu-id="b11dd-118">**Stop**</span></span>  
 <span data-ttu-id="b11dd-119">패키지 업그레이드를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-119">Stop the package upgrade.</span></span>  
  
 <span data-ttu-id="b11dd-120">**Report**</span><span class="sxs-lookup"><span data-stu-id="b11dd-120">**Report**</span></span>  
 <span data-ttu-id="b11dd-121">패키지 업그레이드 결과가 포함된 보고서의 처리 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-121">Select what you want to do with the report that contains the results of the package upgrade:</span></span>  
  
-   <span data-ttu-id="b11dd-122">보고서를 온라인으로 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-122">View the report online.</span></span>  
  
-   <span data-ttu-id="b11dd-123">보고서를 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-123">Save the report to a file.</span></span>  
  
-   <span data-ttu-id="b11dd-124">보고서를 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-124">Copy the report to the Clipboard</span></span>  
  
-   <span data-ttu-id="b11dd-125">보고서를 전자 메일 메시지로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b11dd-125">Send the report as an e-mail message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b11dd-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b11dd-126">See Also</span></span>  
 [<span data-ttu-id="b11dd-127">Integration Services 패키지 업그레이드</span><span class="sxs-lookup"><span data-stu-id="b11dd-127">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
