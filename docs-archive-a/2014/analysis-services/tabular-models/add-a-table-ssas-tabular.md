---
title: 테이블 추가 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d713c432-db99-4983-acc1-52b0fdd58bd6
author: minewiskan
ms.author: owend
ms.openlocfilehash: a80c22c992a89ed2cb3db84809b47a7cd08cb514
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653526"
---
# <a name="add-a-table-ssas-tabular"></a><span data-ttu-id="760f7-102">테이블 추가(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="760f7-102">Add a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="760f7-103">이 항목에서는 이전에 데이터를 모델로 가져왔던 데이터 원본의 테이블을 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-103">This topic describes how to add a table from a data source from which you have previously imported data into your model.</span></span> <span data-ttu-id="760f7-104">같은 데이터 원본의 테이블을 추가하려면 기존 데이터 원본 연결을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-104">To add a table from the same data source, you can use the existing data source connection.</span></span> <span data-ttu-id="760f7-105">단일 데이터 원본에서 임의 개수의 테이블을 가져올 때는 항상 단일 연결을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-105">It is recommended you always use a single connection when importing any number of tables from a single data source.</span></span>  
  
### <a name="to-add-a-table-from-an-existing-data-source"></a><span data-ttu-id="760f7-106">기존 데이터 원본의 테이블을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="760f7-106">To add a table from an existing data source</span></span>  
  
1.  <span data-ttu-id="760f7-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭한 다음 **기존 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="760f7-108">**기존 연결** 페이지에서 추가할 테이블이 있는 데이터 원본에 대한 연결을 선택한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-108">On the **Existing Connections** page, select the connection to the data source that has the table you want to add, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="760f7-109">**테이블 및 뷰 선택** 페이지에서 모델에 추가할 데이터 원본의 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-109">On the **Select Tables and Views** page, select the table from the data source you want to add to your model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="760f7-110">**테이블 및 뷰 선택** 페이지에서는 이전에 가져온 테이블이 선택된 것으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-110">The **Select Tables and Views** page will not show tables that were previously imported as checked.</span></span>  <span data-ttu-id="760f7-111">이 연결을 사용하여 이전에 가져온 테이블을 선택했는데 해당 테이블에 다른 이름을 지정하지 않은 경우 이름에 1이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-111">If you select a table that was previously imported using this connection, and you did not give the table a different friendly name, a 1 will be appended to the friendly name.</span></span> <span data-ttu-id="760f7-112">이 연결을 사용하여 이전에 가져온 테이블을 다시 선택할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-112">You do not need to re-select any tables that were previously imported by using this connection.</span></span>  
  
4.  <span data-ttu-id="760f7-113">필요한 경우 **미리 보기 및 필터**를 사용하여 특정 열만 선택하거나 가져올 데이터에 필터를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-113">If necessary, use **Preview & Filter** to select only certain columns or apply filters to the data to be imported.</span></span>  
  
5.  <span data-ttu-id="760f7-114">**마침** 을 클릭하여 새 테이블을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-114">Click **Finish** to import the new table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="760f7-115">단일 데이터 원본에서 여러 테이블을 동시에 가져올 때는 원본에 있는 해당 테이블 간의 관계가 모델에서 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-115">When importing multiple tables at the same time from a single data source, any relationships between those tables at the source will automatically be created in the model.</span></span> <span data-ttu-id="760f7-116">그러나 나중에 테이블을 추가할 때는 새로 추가한 테이블과 이전에 가져온 테이블 간에 모델에서 관계를 수동으로 만들어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="760f7-116">When adding a table later; however, you may need to manually create relationships in the model between newly added tables and the tables that were previously imported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="760f7-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="760f7-117">See Also</span></span>  
 <span data-ttu-id="760f7-118">[SSAS 테이블 형식&#41;&#40;데이터 가져오기](../import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="760f7-118">[Import Data &#40;SSAS Tabular&#41;](../import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="760f7-119">테이블 삭제&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="760f7-119">Delete a Table &#40;SSAS Tabular&#41;</span></span>](delete-a-table-ssas-tabular.md)  
  
  
