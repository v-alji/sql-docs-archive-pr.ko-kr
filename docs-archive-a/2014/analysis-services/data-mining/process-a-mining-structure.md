---
title: 마이닝 구조 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], processing
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76d25a927ae61ee5ffadf4ca21073a1c04cdb542
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734615"
---
# <a name="process-a-mining-structure"></a><span data-ttu-id="e9a9a-102">마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="e9a9a-102">Process a Mining Structure</span></span>
  <span data-ttu-id="e9a9a-103">마이닝 구조와 연결된 마이닝 모델을 검색하거나 사용하려면 먼저 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 배포하고 마이닝 구조와 마이닝 모델을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-103">Before you can browse or work with the mining models that are associated with a mining structure, you have to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project and process the mining structure and mining models.</span></span> <span data-ttu-id="e9a9a-104">마이닝 구조나 마이닝 모델을 변경하는 경우 이를 다시 배포하고 처리하라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-104">Also, if you make a change to the mining structure or mining models, you will be prompted to redeploy and process them.</span></span> <span data-ttu-id="e9a9a-105">**의 데이터 마이닝 디자이너에 있는** 마이닝 구조 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 탭에서 구조를 처리하면 연결된 모델이 모두 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-105">Processing the structure in the **Mining Structure** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] processes all the associated models.</span></span>  
  
 <span data-ttu-id="e9a9a-106">다음 도구를 사용하여 마이닝 구조를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-106">You can process a mining structure by using these tools:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   <span data-ttu-id="e9a9a-107">XMLA: Process 명령</span><span class="sxs-lookup"><span data-stu-id="e9a9a-107">XMLA: Process command</span></span>  
  
 <span data-ttu-id="e9a9a-108">개별 모델을 처리하는 방법에 대한 자세한 내용은 [마이닝 모델 처리](process-a-mining-model.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-108">For information about how to process individual models, see [Process a Mining Model](process-a-mining-model.md).</span></span>  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a><span data-ttu-id="e9a9a-109">SQL Server Data Tools를 사용하여 마이닝 구조와 연결된 마이닝 모델을 모두 처리하려면</span><span class="sxs-lookup"><span data-stu-id="e9a9a-109">To process a mining structure and all associated mining models using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="e9a9a-110">**의** 마이닝 모델 **메뉴 항목에서** 마이닝 구조 및 모든 모델 처리 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-110">Select **Process Mining Structure and All Models** from the **Mining Model** menu item in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
     <span data-ttu-id="e9a9a-111">구조를 변경하는 경우 모델을 처리하기 전에 구조를 다시 배포하라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-111">If you made changes to the structure, you will be prompted to redeploy the structure before processing the models.</span></span> <span data-ttu-id="e9a9a-112">**예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-112">Click **Yes**.</span></span>  
  
2.  <span data-ttu-id="e9a9a-113">**마이닝 구조 처리 \<structure> -** 대화 상자에서 **실행** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-113">Click **Run** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
     <span data-ttu-id="e9a9a-114">**처리 진행률** 대화 상자가 열리고 모델 처리 세부 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-114">The **Process Progress** dialog box opens to display the details of model processing.</span></span>  
  
3.  <span data-ttu-id="e9a9a-115">모델 처리가 완료되면 **처리 진행률** 대화 상자에서 **닫기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-115">Click **Close** in the **Process Progress** dialog box after the models have completed processing.</span></span>  
  
4.  <span data-ttu-id="e9a9a-116">**마이닝 구조 처리 \<structure> -** 대화 상자에서 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9a9a-116">Click **Close** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a9a-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9a9a-117">See Also</span></span>  
 [<span data-ttu-id="e9a9a-118">마이닝 구조 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="e9a9a-118">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
