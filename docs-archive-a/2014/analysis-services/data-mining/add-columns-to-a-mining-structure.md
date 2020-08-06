---
title: 마이닝 구조에 열 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- columns [data mining], mining structure columns
- adding columns
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 093d78b36ab3aae6600b890a8137025c9dc9134e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653058"
---
# <a name="add-columns-to-a-mining-structure"></a><span data-ttu-id="76873-102">마이닝 구조에 열 추가</span><span class="sxs-lookup"><span data-stu-id="76873-102">Add Columns to a Mining Structure</span></span>
  <span data-ttu-id="76873-103">데이터 마이닝 마법사에서 마이닝 구조를 정의한 후 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 의 데이터 마이닝 디자이너를 사용하여 마이닝 구조에 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76873-103">Use Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to add columns to a mining structure after you have defined it in the Data Mining Wizard.</span></span> <span data-ttu-id="76873-104">마이닝 구조 정의에 사용된 데이터 원본 뷰에 있는 열을 모두 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76873-104">You can add any column that exists in the data source view that was used to define the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76873-105">마이닝 구조에 열의 여러 복사본을 추가할 수 있지만, 원본과 파생 열 간에 잘못된 상관 관계를 방지하려면 동일한 모델 내에서 두 개 이상의 열 인스턴스를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="76873-105">You can add multiple copies of columns to a mining structure; however, you should avoid using more than one instance of the column within the same model, to avoid false correlations between the source and the derived column.</span></span>  
  
### <a name="to-add-a-column-to-a-mining-structure"></a><span data-ttu-id="76873-106">마이닝 구조에 열을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="76873-106">To add a column to a mining structure</span></span>  
  
1.  <span data-ttu-id="76873-107">데이터 마이닝 디자이너에서 **마이닝 구조** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76873-107">Select the **Mining Structure** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="76873-108">마이닝 구조를 마우스 오른쪽 단추로 클릭하고 **열 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76873-108">Right-click the mining structure and select **Add a Column**.</span></span>  
  
     <span data-ttu-id="76873-109">**열 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="76873-109">The **Select a Column** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="76873-110">**원본 테이블**에서 열이 있는 데이터 원본 뷰의 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76873-110">Under **Source table**, select the table in the data source view where the column resides.</span></span>  
  
4.  <span data-ttu-id="76873-111">**원본 열**에서 마이닝 구조에 추가할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76873-111">Under **Source column**, select the column that you want to add to the mining structure.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="76873-112">이미 있는 열을 추가하면 이름에 "1"이 붙은 복사본이 구조에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="76873-112">If you add a column that already exists, a copy will be included in the structure, and the name appended with a "1".</span></span> <span data-ttu-id="76873-113">마이닝 구조 열의 **이름** 속성에 새 이름을 입력하여 복사된 열의 이름을 보다 설명적인 이름으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76873-113">You can change the name of the copied column to something more descriptive by typing a new name in the **Name** property of the mining structure column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76873-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76873-114">See Also</span></span>  
 [<span data-ttu-id="76873-115">마이닝 구조 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="76873-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
