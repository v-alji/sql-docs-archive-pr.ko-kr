---
title: 큐브 마법사를 사용 하 여 큐브 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], creating
ms.assetid: d46d659c-3a4e-4364-94ac-f5eb6ba0ec25
author: minewiskan
ms.author: owend
ms.openlocfilehash: 441c296c0fd71b2a9c2b8332743da6224839a471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737096"
---
# <a name="create-a-cube-using-the-cube-wizard"></a><span data-ttu-id="95fec-102">큐브 마법사를 사용하여 큐브 만들기</span><span class="sxs-lookup"><span data-stu-id="95fec-102">Create a Cube Using the Cube Wizard</span></span>
  <span data-ttu-id="95fec-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 큐브 마법사를 사용하여 새 큐브를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-103">You can create a new cube by using the Cube Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-create-a-new-cube"></a><span data-ttu-id="95fec-104">새 큐브를 만들려면</span><span class="sxs-lookup"><span data-stu-id="95fec-104">To create a new cube</span></span>  
  
1.  <span data-ttu-id="95fec-105">**솔루션 탐색기**에서 **큐브**를 마우스 오른쪽 단추로 클릭 한 다음 **새 큐브**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-105">In **Solution Explorer**, right-click **Cubes**, and then click **New Cube**.</span></span>  
  
2.  <span data-ttu-id="95fec-106">큐브 마법사의 **생성 방법 선택** 페이지에서 **기존 테이블 사용**을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-106">On the **Select Creation Method** page of the Cube Wizard, select **Use existing tables**, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="95fec-107">기존 테이블 없이 큐브를 만들어야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-107">You might occasionally have to create a cube without using existing tables.</span></span> <span data-ttu-id="95fec-108">빈 큐브를 만들려면 **빈 큐브 만들기**를 선택하고</span><span class="sxs-lookup"><span data-stu-id="95fec-108">To create an empty cube, select **Create an empty cube**.</span></span> <span data-ttu-id="95fec-109">테이블을 생성하려면 **데이터 원본에 테이블 생성**을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="95fec-109">To generate tables, select **Generate tables in the data source**.</span></span>  
  
3.  <span data-ttu-id="95fec-110">**측정값 그룹 테이블 선택** 페이지에서 다음 절차를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-110">On the **Select Measure Group Tables** page, do the following procedures:</span></span>  
  
    1.  <span data-ttu-id="95fec-111">**데이터 원본 뷰** 목록에서 데이터 원본 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-111">In the **Data source view** list, select a data source view.</span></span>  
  
    2.  <span data-ttu-id="95fec-112">**측정값 그룹 테이블** 목록에서 측정값 그룹을 만드는 데 사용할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-112">In the **Measure group tables** list, select the tables that will be used to create measure groups.</span></span>  
  
    3.  <span data-ttu-id="95fec-113">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-113">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="95fec-114">**측정값 선택** 페이지에서 큐브에 포함할 측정값을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-114">On the **Select Measures** page, select the measures that you want to include in the cube, and then click **Next**.</span></span>  
  
     <span data-ttu-id="95fec-115">경우에 따라 측정값 및 측정값 그룹의 이름을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-115">Optionally, you can change the names of the measures and measure groups.</span></span>  
  
5.  <span data-ttu-id="95fec-116">**기존 차원 선택** 페이지에서 큐브에 포함할 기존 차원을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-116">On the **Select Existing Dimensions** page, select the existing dimensions to include in the cube, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="95fec-117"> 선택한 측정값 그룹의 데이터베이스에 차원이 이미 있으면 **기존 차원 선택** 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-117">The **Select Existing Dimensions** page appears if dimensions already exist in the database for any of the selected measure groups.</span></span>  
  
6.  <span data-ttu-id="95fec-118">**새 차원 선택** 페이지에서 새로 만들 차원을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-118">On the **Select New Dimensions** page, select the new dimensions to create, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="95fec-119"> 아무 테이블이나 차원 테이블로 사용할 수 있고 기존 차원에서 이러한 테이블을 아직 사용하지 않은 경우 **새 차원 선택** 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-119">The **Select New Dimensions** page appears if any tables would be good candidates for dimension tables, and the tables have not already been used by existing dimensions.</span></span>  
  
7.  <span data-ttu-id="95fec-120">**누락 차원 키 선택** 페이지에서 차원의 키를 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-120">On the **Select Missing Dimension Keys** page, select a key for the dimension, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="95fec-121"> 지정한 모든 차원 테이블에 키가 정의되어 있지 않으면 **누락 차원 키 선택** 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-121">The **Select Missing Dimension Keys** page appears if any of the dimension tables that you specified do not have a key defined.</span></span>  
  
8.  <span data-ttu-id="95fec-122">**마법사 완료** 페이지에서 새 큐브의 이름을 입력하고 큐브 구조를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-122">On the **Completing the Wizard** page, enter a name for the new cube and review the cube structure.</span></span> <span data-ttu-id="95fec-123">변경하려면 **뒤로**를 클릭하고 변경하지 않으려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-123">If you want to make changes, click **Back**; otherwise, click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="95fec-124">큐브 마법사를 완료한 후 큐브 디자이너를 사용하여 큐브를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-124">You can use Cube Designer after you complete the Cube Wizard to configure the cube.</span></span> <span data-ttu-id="95fec-125">또한 차원 디자이너를 사용하여 만든 차원에서 특성과 계층을 추가, 제거 및 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fec-125">You can also use Dimension Designer to add, remove, and configure attributes and hierarchies in the dimensions that you created.</span></span>  
  
  
