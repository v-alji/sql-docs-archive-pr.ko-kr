---
title: 마이닝 구조에서 열 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44ad1de08d57d00fd9798e1ceeddb85d146d7111
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639102"
---
# <a name="remove-columns-from-a-mining-structure"></a><span data-ttu-id="8562f-102">마이닝 구조에서 열 제거</span><span class="sxs-lookup"><span data-stu-id="8562f-102">Remove Columns from a Mining Structure</span></span>
  <span data-ttu-id="8562f-103">마이닝 구조를 만든 후 데이터 마이닝 디자이너를 사용하여 해당 구조에서 열을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8562f-103">You can use Data Mining Designer to remove columns from a mining structure after the structure has already been created.</span></span> <span data-ttu-id="8562f-104">마이닝 구조 열을 제거하는 이유는 다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8562f-104">Reasons to remove a mining structure column might include the following:</span></span>  
  
-   <span data-ttu-id="8562f-105">마이닝 구조에 한 열의 여러 복사본이 포함되어 있으며 모델에 중복 데이터를 사용하지 않으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8562f-105">The mining structure contains multiple copies of a column and you want to avoid the use of duplicate data in a model.</span></span>  
  
-   <span data-ttu-id="8562f-106">데이터를 보호해야 하지만 드릴스루를 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8562f-106">The data should be protected, but drillthrough has been enabled.</span></span>  
  
-   <span data-ttu-id="8562f-107">데이터가 모델링에 사용되지 않으며 데이터를 처리해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8562f-107">The data is unused in modeling and should not be processed.</span></span>  
  
 <span data-ttu-id="8562f-108">마이닝 구조에서 열을 삭제하면 데이터 원본 뷰 또는 외부 데이터에서는 열이 변경되지 않고 메타데이터만 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="8562f-108">Deleting a column from the mining structure does not change the column in the data source view or in the external data; only metadata is deleted.</span></span> <span data-ttu-id="8562f-109">그러나 마이닝 구조에서 사용되는 열을 변경하면 해당 구조 및 해당 구조를 기반으로 하는 모델을 모두 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8562f-109">However, when you change the columns used in a mining structure, you must reprocess the structure and any models based on it.</span></span>  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a><span data-ttu-id="8562f-110">마이닝 구조에서 열을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="8562f-110">To remove a column from the mining structure</span></span>  
  
1.  <span data-ttu-id="8562f-111">데이터 마이닝 디자이너에서 **마이닝 구조** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8562f-111">Select the **Mining Structure** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="8562f-112">마이닝 구조 트리를 확장하여 모든 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8562f-112">Expand the tree for the mining structure, to show all the columns.</span></span>  
  
3.  <span data-ttu-id="8562f-113">삭제할 열을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8562f-113">Right-click the column that you want to delete, and then select **Delete**.</span></span>  
  
4.  <span data-ttu-id="8562f-114">**개체 삭제** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8562f-114">In the **Delete Objects** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8562f-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8562f-115">See Also</span></span>  
 [<span data-ttu-id="8562f-116">마이닝 구조 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="8562f-116">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
