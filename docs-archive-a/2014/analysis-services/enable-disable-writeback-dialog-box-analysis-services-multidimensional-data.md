---
title: 사용-쓰기 저장 안 함 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitiondesigner.writebackenabledisable.f1
ms.assetid: 2d254393-3f0d-4b70-8b98-87159f9f3639
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54ee4597ee78f45682730bd0e8d7119d204eaf2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661394"
---
# <a name="enable-disable-writeback-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="262ba-102">사용-쓰기 저장 안 함 대화 상자 (Analysis Services 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="262ba-102">Enable-Disable Writeback Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="262ba-103">**쓰기 저장 사용/사용 안 함** 대화 상자를 사용하면 큐브의 측정값 그룹에 대해 쓰기 저장을 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-103">The **Enable/Disable Writeback** dialog box enables or disables writeback for a measure group in a cube.</span></span> <span data-ttu-id="262ba-104">측정값 그룹에 대해 쓰기 저장을 설정하면 쓰기 저장 파티션이 정의되고 해당 측정값 그룹에 대한 쓰기 저장 테이블이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-104">Enabling writeback on a measure group defines a writeback partition and creates a writeback table for that measure group.</span></span> <span data-ttu-id="262ba-105">측정값 그룹에 대해 쓰기 저장을 해제하면 쓰기 저장 파티션이 제거되지만 예기치 않은 데이터 손실을 방지하기 위해 쓰기 저장 테이블은 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-105">Disabling writeback on a measure group removes the writeback partition but does not delete the writeback table, to avoid unanticipated data loss.</span></span> <span data-ttu-id="262ba-106">다음 작업을 수행하면 **쓰기 저장 사용/사용 안 함** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-106">The **Enable/Disable Writeback** dialog box is displayed by:</span></span>  
  
-   <span data-ttu-id="262ba-107">큐브 디자이너의 **파티션** 탭에서 **측정값 그룹** 창의 **쓰기 저장 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-107">Clicking **Writeback Settings** in the **Measure Groups** pane on the **Partitions** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="262ba-108">큐브 디자이너의 **파티션** 탭에 있는 **측정값 그룹** 창에서 **파티션** 표에 있는 파티션을 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **쓰기 저장 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-108">Right-clicking a partition in the **Partitions** grid in the **Measure Groups** pane on the **Partitions** tab in Cube Designer and selecting **Writeback Settings** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="262ba-109">옵션</span><span class="sxs-lookup"><span data-stu-id="262ba-109">Options</span></span>  
 <span data-ttu-id="262ba-110">**테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="262ba-110">**Table name**</span></span>  
 <span data-ttu-id="262ba-111">선택한 파티션에 대해 만들려는 쓰기 저장 테이블의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-111">Type the name of the writeback table to create for the selected partition.</span></span> <span data-ttu-id="262ba-112">쓰기 저장 테이블은 클라이언트 애플리케이션의 측정값 그룹 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-112">The writeback table stores the changes made to the measure group from a client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="262ba-113">쓰기 저장을 설정하지 않으면 이 옵션도 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-113">This option is disabled if writeback is not enabled.</span></span>  
  
 <span data-ttu-id="262ba-114">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="262ba-114">**Data source**</span></span>  
 <span data-ttu-id="262ba-115">쓰기 저장 테이블을 포함할 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-115">Select the data source to contain the writeback table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="262ba-116">쓰기 저장을 설정하지 않으면 이 옵션도 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-116">This option is disabled if writeback is not enabled.</span></span>  
  
 <span data-ttu-id="262ba-117">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="262ba-117">**New**</span></span>  
 <span data-ttu-id="262ba-118">**연결 관리자** 대화 상자를 표시하고 쓰기 저장 테이블을 포함할 새 데이터 원본을 정의하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-118">Click to display the **Connection Manager** dialog box and define a new data source to contain the writeback table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="262ba-119">쓰기 저장을 설정하지 않으면 이 옵션도 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="262ba-119">This option is disabled if writeback is not enabled.</span></span>  
  
  
