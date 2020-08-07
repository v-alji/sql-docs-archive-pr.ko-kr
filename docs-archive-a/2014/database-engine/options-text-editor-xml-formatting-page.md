---
title: 옵션 (텍스트 편집기-XML-서식 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
author: rothja
ms.author: jroth
ms.openlocfilehash: dce36142fe9974c0167fca700c509642e05d89b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732900"
---
# <a name="options-text-editor---xml---formatting-page"></a><span data-ttu-id="7df4a-102">옵션(텍스트 편집기 - XML - 서식 페이지)</span><span class="sxs-lookup"><span data-stu-id="7df4a-102">Options (Text Editor - XML - Formatting Page)</span></span>

<span data-ttu-id="7df4a-103">이 대화 상자를 사용하여 XML 편집기의 서식 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-103">This dialog box allows you to specify the formatting settings for the XML Editor.</span></span> <span data-ttu-id="7df4a-104">**옵션** 대화 상자는 **도구** 메뉴에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-104">You can access the **Options** dialog box from the **Tools** menu.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="7df4a-105">이러한 설정은 **옵션** 대화 상자에서 **텍스트 편집기** 폴더,**XML** 폴더, **서식** 옵션을 차례로 선택할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-105">These settings are available when you select the **Text Editor** folder, the **XML** folder, and then the **Formatting** option from the **Options** dialog box.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="7df4a-106">특성</span><span class="sxs-lookup"><span data-stu-id="7df4a-106">Attributes</span></span>  
 <span data-ttu-id="7df4a-107">**특성 수동 서식 유지**</span><span class="sxs-lookup"><span data-stu-id="7df4a-107">**Preserve manual attribute formatting**</span></span>  
 <span data-ttu-id="7df4a-108">특성 서식을 다시 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7df4a-108">Do not reformat attributes.</span></span> <span data-ttu-id="7df4a-109">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-109">This is the default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7df4a-110">특성이 여러 줄로 된 경우 편집기에서 상위 요소의 들여쓰기에 맞게 특성의 각 줄을 들여씁니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-110">If the attributes are on multiple lines, the editor indents each line of attributes to match the indentation of the parent element.</span></span>  
  
 <span data-ttu-id="7df4a-111">**별도의 줄에 각 특성 정렬**</span><span class="sxs-lookup"><span data-stu-id="7df4a-111">**Align attributes each on a separate line**</span></span>  
 <span data-ttu-id="7df4a-112">첫 번째 특성의 들여쓰기에 맞게 두 번째 및 이후의 특성을 세로로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-112">Align the second and subsequent attributes vertically to match the indentation of the first attribute.</span></span> <span data-ttu-id="7df4a-113">다음 XML 텍스트는 특성 정렬 방법의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-113">The following XML text is an example of how the attributes would be aligned.</span></span>  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a><span data-ttu-id="7df4a-114">자동 서식 다시 설정</span><span class="sxs-lookup"><span data-stu-id="7df4a-114">Auto Reformat</span></span>  
 <span data-ttu-id="7df4a-115">**클립보드에서 붙여 넣을 때**</span><span class="sxs-lookup"><span data-stu-id="7df4a-115">**On paste from clipboard.**</span></span>  
 <span data-ttu-id="7df4a-116">클립보드에서 붙여 넣은 XML 텍스트 서식을 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-116">Reformat XML text pasted from the clipboard.</span></span>  
  
 <span data-ttu-id="7df4a-117">**끝 태그가 완료될 때**</span><span class="sxs-lookup"><span data-stu-id="7df4a-117">**On completion of end tag**</span></span>  
 <span data-ttu-id="7df4a-118">끝 태그가 완료될 때 요소 서식을 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-118">Reformat the element when the end tag is completed.</span></span>  
  
## <a name="mixed-content"></a><span data-ttu-id="7df4a-119">혼합 내용</span><span class="sxs-lookup"><span data-stu-id="7df4a-119">Mixed Content</span></span>  
 <span data-ttu-id="7df4a-120">**기본값으로 혼합된 콘텐츠 서식 지정**</span><span class="sxs-lookup"><span data-stu-id="7df4a-120">**Format mixed content by default.**</span></span>  
 <span data-ttu-id="7df4a-121">`xml:space="preserve"` 범위에 콘텐츠가 있을 때를 제외하고 혼합된 콘텐츠 서식을 다시 설정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-121">Attempt to reformat mixed content, except when the content is found in an `xml:space="preserve"` scope.</span></span> <span data-ttu-id="7df4a-122">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-122">This is the default.</span></span>  
  
 <span data-ttu-id="7df4a-123">요소에 텍스트와 마크업이 혼합되어 있으면 콘텐츠가 혼합된 콘텐츠로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-123">If an element contains a mix of text and markup, the contents are considered to be mixed content.</span></span> <span data-ttu-id="7df4a-124">다음은 혼합된 콘텐츠가 있는 요소의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="7df4a-124">Following is an example of an element with mixed content.</span></span>  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \</dir>  
  
## <a name="see-also"></a><span data-ttu-id="7df4a-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7df4a-125">See Also</span></span>  
 [<span data-ttu-id="7df4a-126">XML 편집기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="7df4a-126">XML Editor &#40;SQL Server Management Studio&#41;</span></span>](../ssms/sql-server-management-studio-ssms.md)  
