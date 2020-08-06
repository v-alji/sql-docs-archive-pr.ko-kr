---
title: 기존 데이터 원본 연결 편집 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.selexistconn.f1
ms.assetid: 97e63f18-a01d-4c91-a411-e7e6d40a0647
author: minewiskan
ms.author: owend
ms.openlocfilehash: 675a0d1119e25a92231d3e74a79739cb2e96b6d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659709"
---
# <a name="edit-an-existing-data-source-connection-ssas-tabular"></a><span data-ttu-id="cf9ef-102">기존 데이터 원본 연결 편집(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="cf9ef-102">Edit an Existing Data Source Connection (SSAS Tabular)</span></span>
  <span data-ttu-id="cf9ef-103">이 항목에서는 테이블 형식 모델에서 기존 데이터 원본 연결의 속성을 편집하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-103">This topic describes how to edit the properties of an existing data source connection in a tabular model.</span></span>  
  
 <span data-ttu-id="cf9ef-104">외부 데이터 원본에 대한 연결을 만든 후 나중에 다음과 같은 방법으로 연결을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-104">After you have created a connection to an external data source, you can later modify that connection in these ways:</span></span>  
  
-   <span data-ttu-id="cf9ef-105">원본으로 사용된 파일, 피드 또는 데이터베이스, 해당 속성 또는 기타 공급자별 연결 옵션을 비롯한 연결 정보를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-105">You can change the connection information, including the file, feed, or database used as a source, its properties, or other provider-specific connection options.</span></span>  
  
-   <span data-ttu-id="cf9ef-106">테이블 및 열 매핑을 변경하고 더 이상 사용되지 않는 열에 대한 참조를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-106">You can change table and column mappings, and remove references to columns that are no longer used.</span></span>  
  
-   <span data-ttu-id="cf9ef-107">외부 데이터 원본에서 가져오는 테이블, 뷰 또는 열을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-107">You can change the tables, views, or columns that you get from the external data source.</span></span>  
  
## <a name="modify-a-connection"></a><span data-ttu-id="cf9ef-108">연결 수정</span><span class="sxs-lookup"><span data-stu-id="cf9ef-108">Modify a Connection</span></span>  
 <span data-ttu-id="cf9ef-109">이 절차에서는 데이터베이스 데이터 원본 연결을 수정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-109">This procedure describes how to modify a database data source connection.</span></span> <span data-ttu-id="cf9ef-110">데이터 원본으로 작업하는 데 사용할 수 있는 일부 옵션은 데이터 원본의 유형에 따라 다르지만 그러한 차이를 쉽게 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-110">Some options for working with data sources differ depending on the data source type; however, you should be able to easily identify those differences.</span></span>  
  
#### <a name="to-change-the-external-data-source-used-by-a-current-connection"></a><span data-ttu-id="cf9ef-111">현재 연결에 사용되는 외부 데이터 원본을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="cf9ef-111">To change the external data source used by a current connection</span></span>  
  
1.  <span data-ttu-id="cf9ef-112">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭한 다음 **기존 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="cf9ef-113">수정하려는 데이터 원본 연결을 선택한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-113">Select the data source connection you want to modify, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="cf9ef-114">**연결 편집** 대화 상자에서 **찾아보기** 를 클릭하여 유형은 같지만 이름이나 위치는 같지 않은 다른 데이터베이스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-114">In the **Edit Connection** dialog box, click **Browse** to locate another database of the same type but with a different name or location.</span></span>  
  
     <span data-ttu-id="cf9ef-115">데이터베이스 파일을 변경하면 테이블을 저장하고 새로 고쳐야 새 데이터를 볼 수 있다는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-115">As soon as you change the database file, a message appears indicating that you need to save and refresh the tables in order to see the new data.</span></span>  
  
4.  <span data-ttu-id="cf9ef-116">**저장**을 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-116">Click **Save**, and then click **Close**.</span></span>  
  
5.  <span data-ttu-id="cf9ef-117">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **모델**을 클릭하고 **처리**를 클릭한 다음 **모두 처리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-117">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model**, click **Process**, and then click **Process All**.</span></span>  
  
     <span data-ttu-id="cf9ef-118">새 데이터 원본을 사용하여 테이블이 다시 처리되지만 원래 선택된 데이터는 그대로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-118">The tables are re-processed using the new data source, but with the original data selections.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cf9ef-119">새 데이터 원본에 원래 데이터 원본에는 없는 추가 테이블이 있는 경우 변경한 연결을 다시 열고 해당 테이블을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-119">If the new data source contains any additional tables that were not present in the original data source, you must re-open the changed connection and add the tables.</span></span>  
  
## <a name="edit-table-and-column-mappings-bindings"></a><span data-ttu-id="cf9ef-120">테이블 및 열 매핑(바인딩) 편집</span><span class="sxs-lookup"><span data-stu-id="cf9ef-120">Edit Table and Column Mappings (Bindings)</span></span>  
 <span data-ttu-id="cf9ef-121">이 절차에서는 데이터 원본을 변경한 후 매핑을 편집하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-121">This procedure describes how to edit the mappings after you change a data source.</span></span>  
  
#### <a name="to-edit-column-mappings-when-a-data-source-changes"></a><span data-ttu-id="cf9ef-122">데이터 원본을 변경할 때 열 매핑을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="cf9ef-122">To edit column mappings when a data source changes</span></span>  
  
1.  <span data-ttu-id="cf9ef-123">모델 디자이너에서 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-123">In the model designer, select a table.</span></span>  
  
2.  <span data-ttu-id="cf9ef-124">**테이블** 메뉴를 클릭한 다음 **테이블 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-124">Click on the **Table** menu, and then click **Table Properties**.</span></span>  
  
     <span data-ttu-id="cf9ef-125">선택한 테이블의 이름이 **테이블 이름** 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-125">The name of the selected table is displayed in the **Table Name** box.</span></span> <span data-ttu-id="cf9ef-126">**원본 이름** 상자에는 외부 데이터 원본에 있는 테이블의 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-126">The **Source Name** box contains the name of the table in the external data source.</span></span> <span data-ttu-id="cf9ef-127">원본과 모델에서 열 이름이 서로 다를 경우 **원본** 또는 **모델**옵션을 선택하여 두 열 이름을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-127">If columns are named differently in the source and in the model, you can toggle between the two sets of column names by selecting the options **Source** or **Model**.</span></span>  
  
3.  <span data-ttu-id="cf9ef-128">데이터 원본으로 사용되는 테이블을 변경하려면 **원본 이름**에서 현재 테이블이 아닌 다른 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-128">To change the table that is used as a data source, for **Source Name**, select a different table than the current one.</span></span>  
  
4.  <span data-ttu-id="cf9ef-129">필요한 경우 열 매핑을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-129">Change column mappings if needed:</span></span>  
  
    1.  <span data-ttu-id="cf9ef-130">원본에는 있지만 모델에는 없는 열을 추가하려면 열 이름 옆의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-130">To add columns that are present in the source but not in the model, select the checkbox beside the column name.</span></span>  
  
         <span data-ttu-id="cf9ef-131">다음에 모델을 새로 고칠 때 실제 데이터가 통합 문서에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-131">The actual data will be loaded into the model the next time you refresh.</span></span>  
  
    2.  <span data-ttu-id="cf9ef-132">모델의 일부 열을 현재 데이터 원본에서 더 이상 사용할 수 없는 경우 잘못된 열을 보여 주는 메시지가 알림 영역에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-132">If some columns in the model are no longer available in the current data source, a message appears in the notification area that lists the invalid columns.</span></span> <span data-ttu-id="cf9ef-133">이 경우 별도의 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-133">You do not need to do anything else.</span></span>  
  
5.  <span data-ttu-id="cf9ef-134">**저장** 을 클릭하여 변경 내용을 모델에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-134">Click **Save** to apply the changes to your model.</span></span>  
  
     <span data-ttu-id="cf9ef-135">현재 테이블 속성 집합을 저장하면 테이블을 처리해야 한다는 메시지가 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-135">When you save the current set of table properties, a message may appear indicating that you need to process the tables.</span></span> <span data-ttu-id="cf9ef-136">**처리** 를 클릭하여 업데이트된 데이터를 모델에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cf9ef-136">Click **Process** to load updated data into your model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9ef-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf9ef-137">See Also</span></span>  
 <span data-ttu-id="cf9ef-138">[SSAS 테이블 형식&#41;&#40;데이터 처리](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="cf9ef-138">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="cf9ef-139">지원되는 데이터 원본&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="cf9ef-139">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
