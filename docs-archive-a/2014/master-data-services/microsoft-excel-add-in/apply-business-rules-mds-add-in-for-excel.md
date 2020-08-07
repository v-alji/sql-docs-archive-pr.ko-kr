---
title: 비즈니스 규칙 적용(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aad5ce6bcebb635fa4659c32654d67406d4ba0dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730804"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a><span data-ttu-id="d3a7b-102">비즈니스 규칙 적용(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="d3a7b-102">Apply Business Rules (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="d3a7b-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 에서는 데이터의 유효성을 검사하고 데이터가 유효한지 확인하려는 경우에 비즈니스 규칙을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a7b-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] apply business rules when you want to validate data and confirm that it is valid.</span></span> <span data-ttu-id="d3a7b-104">유효성 검사를 수정하고 데이터를 다시 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3a7b-104">You can correct validations and re-publish the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3a7b-105">데이터 유효성 검사는 데이터를 게시할 때 자동으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a7b-105">Data validation occurs automatically when you publish data.</span></span> <span data-ttu-id="d3a7b-106">자세한 내용은 [유효성 검사 저장 프로시저&#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3a7b-106">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d3a7b-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="d3a7b-107">Prerequisites</span></span>  
 <span data-ttu-id="d3a7b-108">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="d3a7b-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d3a7b-109">**탐색기** 기능 영역에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a7b-109">You must have access to the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="d3a7b-110">MDS 관리 데이터가 포함된 활성 워크시트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a7b-110">You must have an active worksheet that contains MDS-managed data.</span></span>  
  
### <a name="to-apply-business-rules"></a><span data-ttu-id="d3a7b-111">비즈니스 규칙을 적용하려면</span><span class="sxs-lookup"><span data-stu-id="d3a7b-111">To apply business rules</span></span>  
  
1.  <span data-ttu-id="d3a7b-112">**게시 및 유효성 검사** 그룹에서 **규칙 적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a7b-112">In the **Publish and Validate** group, click **Apply Rules**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d3a7b-113">한 번에 유효성이 검사되는 멤버(행) 수는 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]의 설정에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="d3a7b-113">The number of members (rows) that are validated at one time depends on a setting in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="d3a7b-114">자세한 내용은 [Business Rule Settings](../system-settings-master-data-services.md#BusinessRules)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3a7b-114">For more information, see [Business Rule Settings](../system-settings-master-data-services.md#BusinessRules).</span></span>  
  
2.  <span data-ttu-id="d3a7b-115">비즈니스 규칙에 따라 데이터의 유효성을 검사하고 두 개의 상태 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3a7b-115">The data is validated against business rules and two status columns are displayed.</span></span> <span data-ttu-id="d3a7b-116">이러한 열은 자동으로 표시되지 않으며, 열을 표시하려면 **게시 및 검증** 그룹에서 **상태 표시** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3a7b-116">If these columns are not displayed automatically, in the **Publish and Validate** group, click **Show Status** to view them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a7b-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3a7b-117">See Also</span></span>  
 [<span data-ttu-id="d3a7b-118">데이터 &#40;Excel용 MDS 추가 기능&#41;게시</span><span class="sxs-lookup"><span data-stu-id="d3a7b-118">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
