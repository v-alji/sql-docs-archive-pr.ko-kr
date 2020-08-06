---
title: 입력란 방향 설정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d509f1df29203fa5def79b61b74ae9db8f40d204
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639290"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a><span data-ttu-id="79f36-102">입력란 방향 설정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="79f36-102">Set Text Box Orientation (Report Builder and SSRS)</span></span>
  <span data-ttu-id="79f36-103">입력란의 방향을 수평, 수직(위에서 아래로 텍스트 읽기) 또는 270도 회전(아래에서 위로 텍스트 읽기)으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-103">A text box can be oriented in different directions: horizontally, vertically (text reading from top to bottom), or rotated by 270 degrees (text reading from bottom to top).</span></span> <span data-ttu-id="79f36-104">방향이 텍스트가 아니라 입력란에 대해 설정되기 때문에 방향은 입력란의 모든 텍스트에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-104">Because orientation is set on the text box not the text, the orientation applies to all the text in the text box.</span></span> <span data-ttu-id="79f36-105">텍스트의 일부에 대해 다른 방향을 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-105">You cannot specify different orientations for parts of the text.</span></span> <span data-ttu-id="79f36-106">회전된 텍스트를 포함하도록 열 너비와 행 높이를 수동으로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-106">Size the column width and the row height manually to accommodate the rotated text.</span></span>  
  
 <span data-ttu-id="79f36-107">텍스트 방향을 지정 하는 데 사용 하는 WritingMode 속성은 **입력란 속성** 대화 상자에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-107">The WritingMode property, which you use to specify text orientation, is not available in the **Text Box Properties** dialog box.</span></span> <span data-ttu-id="79f36-108">즉, 속성 창을 열고 해당 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-108">You need to open the Properties pane and set the property there.</span></span> <span data-ttu-id="79f36-109">WritingMode 속성에 사용할 수 있는 값은 **가로** (왼쪽에서 오른쪽으로 텍스트 읽기), **세로** (위에서 아래로 텍스트 읽기), **Rotate270** (아래에서 위로 텍스트 읽기)입니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-109">The available values for the WritingMode property are **Horizontal** (text reading left to right), **Vertical** (text reading top to bottom), **Rotate270** (text reading bottom to top).</span></span> <span data-ttu-id="79f36-110">텍스트를 포함하도록 열 너비와 행 높이를 수동으로 조정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-110">You must manually size the column width and the row height to accommodate the text.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a><span data-ttu-id="79f36-111">텍스트 방향을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="79f36-111">To set text orientation</span></span>  
  
1.  <span data-ttu-id="79f36-112">새 보고서를 만들거나 기존 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-112">Create a new report or open an existing report.</span></span>  
  
2.  <span data-ttu-id="79f36-113">속성 창이 열려 있지 않으면 **보기** 탭을 클릭하고 **속성** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-113">If the Properties pane is not open, click the **View** tab and select the **Properties** check box.</span></span>  
  
3.  <span data-ttu-id="79f36-114">텍스트 방향을 변경할 입력란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-114">Click the text box for which you want to change text orientation.</span></span>  
  
4.  <span data-ttu-id="79f36-115">속성 창에서 WritingMode 속성을 찾고 드롭다운 목록에서 텍스트 상자에 적용할 텍스트 방향을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-115">Locate the WritingMode property in the Properties pane and in the drop-down list select the text orientation to apply to the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="79f36-116">속성 창의 속성이 범주로 구성되어 있는 경우 WritingMode는 **지역화** 범주에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-116">When the properties in the Properties pane are organized into categories, WritingMode is in the **Localization** category.</span></span>  
  
5.  <span data-ttu-id="79f36-117">목록 상자에서 **Horizontal**, **Vertical**또는 **Rotate270**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79f36-117">In the list box, select **Horizontal**, **Vertical**, or **Rotate270**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f36-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79f36-118">See Also</span></span>  
 <span data-ttu-id="79f36-119">[텍스트 상자 &#40;보고서 작성기 및 SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="79f36-119">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="79f36-120">자습서: 텍스트 서식 지정&#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="79f36-120">Tutorial: Format Text &#40;Report Builder&#41;</span></span>](../tutorial-format-text-report-builder.md)  
  
  
