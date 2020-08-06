---
title: SQL Server Data Tools에서 패키지 복사 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], copying
- copying packages
- regenerating package GUID
- updating package properties
ms.assetid: 03edc659-e76d-48c0-a749-5f1899b6b507
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bd6ed4dd66ee4755181f5df6f3c1b5466b3f26b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651834"
---
# <a name="copy-a-package-in-sql-server-data-tools"></a><span data-ttu-id="e2514-102">SQL Server Data Tools에서 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="e2514-102">Copy a Package in SQL Server Data Tools</span></span>
  <span data-ttu-id="e2514-103">이 항목에서는 기존 패키지를 복사하여 새 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 만드는 방법과 새 패키지의 `Name` 및 `GUID` 속성을 업데이트하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-103">This topic describes how to create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package by copying an existing package, and how to update the `Name` and `GUID` properties of the new package.</span></span>  
  
### <a name="to-copy-a-package"></a><span data-ttu-id="e2514-104">패키지를 복사하려면</span><span class="sxs-lookup"><span data-stu-id="e2514-104">To copy a package</span></span>  
  
1.  <span data-ttu-id="e2514-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 복사할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package that you want to copy.</span></span>  
  
2.  <span data-ttu-id="e2514-106">솔루션 탐색기에서 패키지를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-106">In Solution Explorer, double-click the package.</span></span>  
  
3.  <span data-ttu-id="e2514-107">복사할 패키지를 솔루션 탐색기에서 선택했는지 또는 패키지가 포함된 SSIS 디자이너의 탭이 활성 상태인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-107">Verify either the package to copy is selected in Solution Explorer or the tab in SSIS Designer that contains the package is the active tab</span></span>  
  
4.  <span data-ttu-id="e2514-108">**파일** 메뉴에서 **다른 이름으로 \<package name> 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-108">On the **File** menu, click **Save \<package name> As**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2514-109">SSIS 디자이너에서 패키지를 열어야 **파일** 메뉴에 **다른 이름으로 저장** 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-109">The package must be opened in SSIS Designer before the **Save As** option appears on the **File** menu.</span></span>  
  
5.  <span data-ttu-id="e2514-110">필요에 따라 다른 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-110">Optionally, browse to a different folder.</span></span>  
  
6.  <span data-ttu-id="e2514-111">패키지 파일 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-111">Update the name of the package file.</span></span> <span data-ttu-id="e2514-112">.dtsx 파일 확장명을 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-112">Make sure that you retain the .dtsx file extension.</span></span>  
  
7.  <span data-ttu-id="e2514-113">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-113">Click **Save**.</span></span>  
  
8.  <span data-ttu-id="e2514-114">프롬프트에서 파일 이름과 일치시킬 패키지 개체의 이름을 업데이트할 것인지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-114">At the prompt, choose whether to update the name of the package object to match the file name.</span></span> <span data-ttu-id="e2514-115">**예**를 클릭 하면 `Name` 패키지의 속성이 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-115">If you click **Yes**, the `Name` property of the package is updated.</span></span> <span data-ttu-id="e2514-116">새 패키지가 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에 추가되고 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-116">The new package is added to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and opened in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
9. <span data-ttu-id="e2514-117">필요에 따라 **제어 흐름** 탭의 배경을 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-117">Optionally, click in the background of the **Control Flow** tab, and the click **Properties**.</span></span>  
  
10. <span data-ttu-id="e2514-118">속성 창에서 ID 속성 값을 클릭한 다음, 드롭다운 목록에서 **\<Generate New ID>** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-118">In the Properties window, click the value of the ID property, and then in the drop-down list click **\<Generate New ID>**.</span></span>  
  
11. <span data-ttu-id="e2514-119">**파일** 메뉴에서 **선택한 항목 저장** 을 클릭하여 새 패키지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e2514-119">On the **File** menu, click **Save Selected Items** to save the new package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2514-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2514-120">See Also</span></span>  
 <span data-ttu-id="e2514-121">[패키지의 복사본 저장](../../2014/integration-services/save-a-copy-of-a-package.md) </span><span class="sxs-lookup"><span data-stu-id="e2514-121">[Save a Copy of a Package](../../2014/integration-services/save-a-copy-of-a-package.md) </span></span>  
 <span data-ttu-id="e2514-122">[SQL Server Data Tools에서 패키지 만들기](create-packages-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e2514-122">[Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="e2514-123">Integration Services&#40;SSIS&#41; 패키지</span><span class="sxs-lookup"><span data-stu-id="e2514-123">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
