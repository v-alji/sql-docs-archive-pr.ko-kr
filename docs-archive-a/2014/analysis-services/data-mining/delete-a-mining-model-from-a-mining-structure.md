---
title: 마이닝 구조에서 마이닝 모델 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72c79dcdccf6225b8e75144f8b090dcab7506c10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659735"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a><span data-ttu-id="b2c1b-102">마이닝 구조에서 마이닝 모델 삭제</span><span class="sxs-lookup"><span data-stu-id="b2c1b-102">Delete a Mining Model from a Mining Structure</span></span>
  <span data-ttu-id="b2c1b-103">데이터 마이닝 디자이너, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 DMX 문을 사용하여 마이닝 모델을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2c1b-103">You can delete mining models by using Data Mining Designer, by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or by using DMX statements.</span></span>  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a><span data-ttu-id="b2c1b-104">SQL Server Data Tools를 사용하여 마이닝 모델 삭제</span><span class="sxs-lookup"><span data-stu-id="b2c1b-104">Delete a mining model using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="b2c1b-105">**에서** 마이닝 모델 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2c1b-105">Select the **Mining Models** tab in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="b2c1b-106">삭제할 모델을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2c1b-106">Right-click the model that you want to delete, and select **Delete**.</span></span>  
  
     <span data-ttu-id="b2c1b-107">**개체 삭제** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b2c1b-107">The **Delete Objects** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="b2c1b-108">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2c1b-108">Click **OK**.</span></span>  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a><span data-ttu-id="b2c1b-109">SQL Server Management Studio를 사용하여 마이닝 모델 삭제</span><span class="sxs-lookup"><span data-stu-id="b2c1b-109">Delete a mining model using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b2c1b-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 모델이 포함된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2c1b-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains the model.</span></span>  
  
2.  <span data-ttu-id="b2c1b-111">**마이닝 구조**를 확장하고 **마이닝 모델**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b2c1b-111">Expand **Mining Structures**, and then expand **Mining Models**.</span></span>  
  
3.  <span data-ttu-id="b2c1b-112">삭제할 모델을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b2c1b-112">Right-click the model you want to delete, and select **Delete**.</span></span>  
  
     <span data-ttu-id="b2c1b-113">모델을 삭제해도 학습 데이터는 삭제되지 않고 모델을 학습할 때 메타데이터 및 패턴만 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2c1b-113">Deleting the model does not delete the training data, only the metadata and any patterns created when you trained the model.</span></span>  
  
### <a name="delete-a-mining-model-using-dmx"></a><span data-ttu-id="b2c1b-114">DMX를 사용하여 마이닝 모델 삭제</span><span class="sxs-lookup"><span data-stu-id="b2c1b-114">Delete a mining model using DMX</span></span>  
  
-   [<span data-ttu-id="b2c1b-115">DROP MINING MODEL&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="b2c1b-115">DROP MINING MODEL &#40;DMX&#41;</span></span>](/sql/dmx/drop-mining-model-dmx)  
  
## <a name="see-also"></a><span data-ttu-id="b2c1b-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b2c1b-116">See Also</span></span>  
 [<span data-ttu-id="b2c1b-117">마이닝 모델 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="b2c1b-117">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
