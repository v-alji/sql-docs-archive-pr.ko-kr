---
title: 데이터 유효성 검사(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f8e97ff6481996b2e16436e1f78478bd234fe6ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651076"
---
# <a name="validating-data-mds-add-in-for-excel"></a><span data-ttu-id="99450-102">데이터 유효성 검사(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="99450-102">Validating Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="99450-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서는 데이터를 게시할 때 두 가지 종류의 유효성 검사가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="99450-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], when you publish data, two types of validation take place:</span></span>  
  
-   <span data-ttu-id="99450-104">정의되어 있는 모든 비즈니스 규칙이 데이터에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="99450-104">Any defined business rules are applied to the data.</span></span>  
  
-   <span data-ttu-id="99450-105">허용되는 특성 값인지를 기준으로 데이터가 검사됩니다(예: 문자 수 또는 데이터 형식).</span><span class="sxs-lookup"><span data-stu-id="99450-105">Data is checked against allowed attribute values (for example, number of characters or type of data).</span></span>  
  
 <span data-ttu-id="99450-106">두 가지 경우 모두 유효한 데이터가 MDS 저장소에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="99450-106">In each case, valid data is published to the MDS repository.</span></span> <span data-ttu-id="99450-107">유효하지 않은 데이터는 강조 표시되고 오류에 대한 자세한 정보가 상태 열에 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-107">Data that is not valid is highlighted, and details of the error can be shown in status columns.</span></span>  
  
## <a name="when-validation-occurs"></a><span data-ttu-id="99450-108">유효성 검사가 수행되는 경우</span><span class="sxs-lookup"><span data-stu-id="99450-108">When Validation Occurs</span></span>  
 <span data-ttu-id="99450-109">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 유효성 검사는 새 데이터나 변경된 데이터를 게시할 때 또는 비즈니스 규칙을 수동으로 적용할 때 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="99450-109">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], validation occurs when you publish new or changed data, or when you manually apply business rules.</span></span>  
  
 <span data-ttu-id="99450-110">비즈니스 규칙이 실패할 경우 데이터가 MDS 저장소에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="99450-110">When business rules fail, the data is still published to the MDS repository.</span></span> <span data-ttu-id="99450-111">입력 유효성 검사가 실패할 경우에는 데이터가 저장소에 게시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-111">When input validation fails, the data is not published to the repository.</span></span>  
  
## <a name="validation-statuses"></a><span data-ttu-id="99450-112">유효성 검사 상태</span><span class="sxs-lookup"><span data-stu-id="99450-112">Validation Statuses</span></span>  
 <span data-ttu-id="99450-113">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 유효성 검사 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-113">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], the following validation statuses are possible.</span></span>  
  
|<span data-ttu-id="99450-114">상태</span><span class="sxs-lookup"><span data-stu-id="99450-114">Status</span></span>|<span data-ttu-id="99450-115">Description</span><span class="sxs-lookup"><span data-stu-id="99450-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="99450-116">오류</span><span class="sxs-lookup"><span data-stu-id="99450-116">Error</span></span>|<span data-ttu-id="99450-117">행에 있는 하나 이상의 값이 MDS 관리자가 정의한 비즈니스 규칙에 대한 유효성 검사에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-117">One or more values in the row failed validation against business rules defined by an MDS administrator.</span></span>|  
|<span data-ttu-id="99450-118">유효성 확인 안 됨</span><span class="sxs-lookup"><span data-stu-id="99450-118">Not Validated</span></span>|<span data-ttu-id="99450-119">행의 값이 비즈니스 규칙에 대해 유효성이 검사되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-119">Values in the row have not yet been validated against business rules.</span></span>|  
|<span data-ttu-id="99450-120">Success</span><span class="sxs-lookup"><span data-stu-id="99450-120">Success</span></span>|<span data-ttu-id="99450-121">행의 모든 값이 비즈니스 규칙에 대한 유효성 검사에 통과했습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-121">All values in the row have passed validation against business rules.</span></span>|  
  
## <a name="input-statuses"></a><span data-ttu-id="99450-122">입력 상태</span><span class="sxs-lookup"><span data-stu-id="99450-122">Input Statuses</span></span>  
 <span data-ttu-id="99450-123">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 입력 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-123">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], the following input statuses are possible</span></span>  
  
|<span data-ttu-id="99450-124">상태</span><span class="sxs-lookup"><span data-stu-id="99450-124">Status</span></span>|<span data-ttu-id="99450-125">Description</span><span class="sxs-lookup"><span data-stu-id="99450-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="99450-126">오류</span><span class="sxs-lookup"><span data-stu-id="99450-126">Error</span></span>|<span data-ttu-id="99450-127">행에 있는 하나 이상의 값이 길이 또는 데이터 형식 같은 시스템 요구 사항을 충족하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-127">One or more values in the row don't meet system requirements like length or data type.</span></span> <span data-ttu-id="99450-128">MDS 저장소에서 값이 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-128">The value is not updated in the MDS repository.</span></span>|  
|<span data-ttu-id="99450-129">새 행</span><span class="sxs-lookup"><span data-stu-id="99450-129">New Row</span></span>|<span data-ttu-id="99450-130">행의 값이 아직 MDS 저장소에 게시되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-130">The values in the row have not yet been published to the MDS repository.</span></span>|  
|<span data-ttu-id="99450-131">읽기 전용</span><span class="sxs-lookup"><span data-stu-id="99450-131">Read Only</span></span>|<span data-ttu-id="99450-132">로그인한 사용자에게 행에 있는 하나 이상의 값에 대한 읽기 전용 권한이 있으며 값을 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-132">The logged in user has Read-only permissions to one or more values in the row and the value(s) cannot be updated.</span></span>|  
|<span data-ttu-id="99450-133">변경 안 됨</span><span class="sxs-lookup"><span data-stu-id="99450-133">Unchanged</span></span>|<span data-ttu-id="99450-134">워크시트에서 행의 어떤 값도 변경되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="99450-134">No values in the row have been changed in the worksheet.</span></span> <span data-ttu-id="99450-135">저장소에서 값이 변경되지 않았다는 의미는 아닙니다. 시트의 최신 데이터를 가져오려면 **연결 및 로드** 그룹에서 **로드 또는 새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99450-135">This does not mean the values in the repository have not changed; to get the latest data in the sheet, in the **Connect and Load** group, click **Load or Refresh**.</span></span><br /><br /> <span data-ttu-id="99450-136">이는 각 행의 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="99450-136">This is the default setting for each row.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="99450-137">관련 작업</span><span class="sxs-lookup"><span data-stu-id="99450-137">Related Tasks</span></span>  
  
|<span data-ttu-id="99450-138">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="99450-138">Task Description</span></span>|<span data-ttu-id="99450-139">항목</span><span class="sxs-lookup"><span data-stu-id="99450-139">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="99450-140">정의된 비즈니스 규칙을 통과하지 못한 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="99450-140">Determine which values do not pass the defined business rules.</span></span>|[<span data-ttu-id="99450-141">비즈니스 규칙 적용&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="99450-141">Apply Business Rules &#40;MDS Add-in for Excel&#41;</span></span>](apply-business-rules-mds-add-in-for-excel.md)|  
|<span data-ttu-id="99450-142">유효성 검사 오류를 수정하고 멤버에 대해 수행된 모든 트랜잭션을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="99450-142">To help correct validation errors, view all transactions that have taken place for a member.</span></span>|[<span data-ttu-id="99450-143">멤버에 대한 모든 주석 또는 트랜잭션 보기&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="99450-143">View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;</span></span>](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="99450-144">관련 내용</span><span class="sxs-lookup"><span data-stu-id="99450-144">Related Content</span></span>  
  
-   [<span data-ttu-id="99450-145">데이터 &#40;Excel용 MDS 추가 기능&#41;게시</span><span class="sxs-lookup"><span data-stu-id="99450-145">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
