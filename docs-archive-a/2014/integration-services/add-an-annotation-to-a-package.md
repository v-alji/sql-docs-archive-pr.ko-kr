---
title: 패키지에 주석 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 8db31e78-e03b-44e6-a307-a1349f52b0c6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8fc482f12328b792c1d0b4262a88a292398d9715
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650259"
---
# <a name="add-an-annotation-to-a-package"></a><span data-ttu-id="0a647-102">패키지에 주석 추가</span><span class="sxs-lookup"><span data-stu-id="0a647-102">Add an Annotation to a Package</span></span>
  <span data-ttu-id="0a647-103">이 절차에서는 패키지에 주석을 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-103">This procedure describes how to add an annotation to a package.</span></span>  
  
### <a name="to-add-an-annotation-to-a-package"></a><span data-ttu-id="0a647-104">패키지에 주석을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="0a647-104">To add an annotation to a package</span></span>  
  
1.  <span data-ttu-id="0a647-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 주석을 추가할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to which you want to add an annotation.</span></span>  
  
2.  <span data-ttu-id="0a647-106">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="0a647-107">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **제어 흐름**, **데이터 흐름**또는 **이벤트 처리기** 탭의 디자인 화면에서 아무 곳이나 마우스 오른쪽 단추로 클릭한 후 **주석 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-107">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, right-click anywhere on the design surface of the **Control Flow**, **Data Flow**, or **Event Handler** tab, and then click **Add Annotation**.</span></span> <span data-ttu-id="0a647-108">탭의 디자인 화면에 텍스트 블록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-108">A text block appears on the design surface of the tab.</span></span>  
  
4.  <span data-ttu-id="0a647-109">텍스트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-109">Add text.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a647-110">텍스트를 추가하지 않은 상태에서 블록 바깥을 클릭하면 텍스트 블록이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-110">If you add no text, the text block is removed when you click outside the block.</span></span>  
  
5.  <span data-ttu-id="0a647-111">주석 텍스트의 크기나 서식을 변경하려면 주석을 마우스 오른쪽 단추로 클릭하고 **텍스트 주석 글꼴 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-111">To change the size or format of the text in the annotation, right-click the annotation and then click **Set Text Annotation Font**.</span></span>  
  
6.  <span data-ttu-id="0a647-112">텍스트 줄을 추가하려면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-112">To add an additional line of text, press ENTER.</span></span>  
  
     <span data-ttu-id="0a647-113">텍스트 줄을 추가하면 주석 상자의 크기가 자동으로 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-113">The annotation box automatically increases in size as you add additional lines of text.</span></span>  
  
7.  <span data-ttu-id="0a647-114">그룹에 주석을 추가하려면 주석을 마우스 오른쪽 단추로 클릭하고 **그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-114">To add an annotation to a group, right-click the annotation and then click **Group**.</span></span>  
  
8.  <span data-ttu-id="0a647-115">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a647-115">To save the updated package, on the **File** menu, click **Save All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a647-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a647-116">See Also</span></span>  
 [<span data-ttu-id="0a647-117">패키지에서 주석 사용</span><span class="sxs-lookup"><span data-stu-id="0a647-117">Use Annotations in Packages</span></span>](use-annotations-in-packages.md)  
  
  
