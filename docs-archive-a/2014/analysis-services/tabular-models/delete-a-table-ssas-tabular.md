---
title: 테이블 삭제 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
author: minewiskan
ms.author: owend
ms.openlocfilehash: c72fa90426440c1be84318a15cf0d761ef16aca8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653513"
---
# <a name="delete-a-table-ssas-tabular"></a><span data-ttu-id="80d85-102">테이블 삭제(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="80d85-102">Delete a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="80d85-103">모델 디자이너의 모델 작업 영역 데이터베이스에서 더 이상 필요하지 않은 테이블을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80d85-103">In the model designer, you can delete tables in your model workspace database that you no longer need.</span></span> <span data-ttu-id="80d85-104">테이블을 삭제하면 원래 원본 데이터는 영향을 받지 않고 가져와서 작업하고 있는 데이터만 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="80d85-104">Deleting a table does not affect the original source data, only the data that you imported and were working with.</span></span> <span data-ttu-id="80d85-105">테이블의 삭제는 실행 취소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80d85-105">You cannot undo the deletion of a table.</span></span>  
  
### <a name="to-delete-a-table"></a><span data-ttu-id="80d85-106">테이블 삭제</span><span class="sxs-lookup"><span data-stu-id="80d85-106">To delete a table</span></span>  
  
-   <span data-ttu-id="80d85-107">삭제하려는 테이블에 대해 모델 디자이너 아래쪽의 탭을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80d85-107">Right-click the tab at the bottom of the model designer for the table that you want to delete, and then click **Delete**.</span></span>  
  
## <a name="considerations-when-deleting-tables"></a><span data-ttu-id="80d85-108">테이블 삭제 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="80d85-108">Considerations when Deleting Tables</span></span>  
  
-   <span data-ttu-id="80d85-109">테이블을 삭제하면 테이블이 있던 전체 탭이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="80d85-109">When you delete a table, the entire tab that the table was on is deleted.</span></span>  
  
-   <span data-ttu-id="80d85-110">해당 테이블과 연결된 측정값의 정의도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="80d85-110">If any measures were associated with that table, the definition of the measure will also be deleted.</span></span>  
  
-   <span data-ttu-id="80d85-111">해당 테이블을 사용하여 계산 열을 만든 경우 해당 테이블의 열도 삭제됩니다. 다른 테이블에서 삭제된 테이블의 열을 사용하는 계산 열에서는 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="80d85-111">If you created any calculated columns using that table, columns in that table are also deleted; any calculated columns in other tables that use columns from the deleted table will display an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d85-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80d85-112">See Also</span></span>  
 [<span data-ttu-id="80d85-113">테이블 및 열&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="80d85-113">Tables and Columns &#40;SSAS Tabular&#41;</span></span>](tables-and-columns-ssas-tabular.md)  
  
  
