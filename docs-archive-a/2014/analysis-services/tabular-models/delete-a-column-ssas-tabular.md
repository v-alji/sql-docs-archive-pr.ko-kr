---
title: 열 삭제 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
author: minewiskan
ms.author: owend
ms.openlocfilehash: 06af0b7fd9879661db95bb2073cced545bb4eef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651917"
---
# <a name="delete-a-column-ssas-tabular"></a><span data-ttu-id="4372e-102">열 삭제(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="4372e-102">Delete a Column (SSAS Tabular)</span></span>
  <span data-ttu-id="4372e-103">이 항목에서는 테이블 형식 모델 테이블에서 열을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4372e-103">This topic describes how to delete a column from a tabular model table.</span></span>  
  
## <a name="delete-a-model-table-column"></a><span data-ttu-id="4372e-104">모델 테이블 열 삭제</span><span class="sxs-lookup"><span data-stu-id="4372e-104">Delete a Model Table Column</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4372e-105">모델 테이블에서 열을 삭제해도 파티션 쿼리 정의에서 열이 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4372e-105">Deleting a column from a model table does not delete the column from a partition query definition.</span></span> <span data-ttu-id="4372e-106">삭제할 열이 파티션의 일부분일 경우 파티션 쿼리 정의에서 수동으로 열을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4372e-106">If the column you are deleting is part of a partition, you must manually delete the column from the partition query definition.</span></span> <span data-ttu-id="4372e-107">파티션 쿼리 정의에서 열을 삭제하지 못하면 열이 쿼리되고 데이터가 반환되지만 작업을 처리하는 동안 모델 테이블에 채워지지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4372e-107">Failure to delete the column from the partition query definition will cause the column to be queried and data returned, but not populated to the model table, during processing operations.</span></span> <span data-ttu-id="4372e-108">자세한 내용은 [파티션&#40;SSAS 테이블 형식&#41;](partitions-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4372e-108">For more information, see [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
#### <a name="to-delete-a-model-table-column"></a><span data-ttu-id="4372e-109">모델 테이블 열을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="4372e-109">To delete a model table column</span></span>  
  
-   <span data-ttu-id="4372e-110">모델 디자이너에서 삭제할 열이 포함된 테이블의 열을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4372e-110">In the model designer, in the table that contains the column you want to delete, right-click on the column, and then click **Delete**.</span></span>  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a><span data-ttu-id="4372e-111">테이블 속성 대화 상자를 사용하여 모델 테이블 열을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="4372e-111">To delete a model table column by using the Table Properties dialog box</span></span>  
  
1.  <span data-ttu-id="4372e-112">모델 디자이너에서 삭제할 열이 포함된 테이블을 클릭하고 **테이블** 메뉴를 클릭한 다음  **테이블 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4372e-112">In the model designer, click on the table which contains the column you want to delete, then click the **Table** menu, and then click  **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="4372e-113">**열 이름 원본**에서 **모델** 을 선택합니다(*원본과 다를 경우 모델 테이블 열 이름 사용*).</span><span class="sxs-lookup"><span data-stu-id="4372e-113">In **Column names from**, select **Model** (*to use model table column names, if different from source*).</span></span>  
  
3.  <span data-ttu-id="4372e-114">**테이블 속성 편집** 대화 상자의 테이블 미리 보기 창에서 삭제할 열을 선택 취소한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4372e-114">In the **Edit Table Properties** dialog box, in the table preview window, uncheck the column you want to delete, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4372e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4372e-115">See Also</span></span>  
 <span data-ttu-id="4372e-116">[테이블에 열 추가 &#40;SSAS 테이블 형식&#41;](add-columns-to-a-table-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="4372e-116">[Add Columns to a Table &#40;SSAS Tabular&#41;](add-columns-to-a-table-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="4372e-117">파티션&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="4372e-117">Partitions &#40;SSAS Tabular&#41;</span></span>](partitions-ssas-tabular.md)  
  
  
