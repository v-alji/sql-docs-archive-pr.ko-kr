---
title: 새 폴더 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9212fc68-f0a6-4f79-83c1-84baf4d1957e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 27c6a82c4911ba42215d4ab7dcafd666ddce5d54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653237"
---
# <a name="new-folder-page-report-manager"></a><span data-ttu-id="b3aec-102">새 폴더 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="b3aec-102">New Folder Page (Report Manager)</span></span>
  <span data-ttu-id="b3aec-103">새 폴더 페이지를 사용하여 보고서 서버 폴더 계층에 새 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-103">Use the New Folder page to create a new folder in the report server folder hierarchy.</span></span> <span data-ttu-id="b3aec-104">이 페이지에서 만드는 폴더는 보고서 서버 데이터베이스에 저장되는 가상 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-104">The folder that you create is a virtual folder that is stored in a report server database.</span></span> <span data-ttu-id="b3aec-105">컴퓨터의 파일 시스템에서는 폴더가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-105">The folder is not created in the file system of your computer.</span></span>  
  
 <span data-ttu-id="b3aec-106">폴더는 현재 위치에서 현재 선택된 폴더의 포함된 폴더로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-106">A folder is created in-place, as a subfolder of the folder that is currently selected.</span></span> <span data-ttu-id="b3aec-107">폴더를 만들려면 우선 폴더를 만들 위치로 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-107">Before creating a folder, you should navigate to the location where you want to create the folder.</span></span>  
  
 <span data-ttu-id="b3aec-108">폴더를 만든 후 폴더의 일반 속성 페이지에서 폴더 이름 및 설명을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-108">After you create a folder, you can modify its name and description through the General properties page of the folder.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="b3aec-109">탐색</span><span class="sxs-lookup"><span data-stu-id="b3aec-109">Navigation</span></span>  
 <span data-ttu-id="b3aec-110">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="b3aec-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-folder-page"></a><span data-ttu-id="b3aec-111">새 폴더 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="b3aec-111">To open the New Folder page</span></span>  
  
1.  <span data-ttu-id="b3aec-112">보고서 관리자를 열고 새 폴더를 만들려는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-112">Open Report Manager, and navigate to the folder in which you want to create a new folder.</span></span>  
  
2.  <span data-ttu-id="b3aec-113">도구 모음에서 **새 폴더**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-113">In the toolbar, click **New Folder**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b3aec-114">옵션</span><span class="sxs-lookup"><span data-stu-id="b3aec-114">Options</span></span>  
 <span data-ttu-id="b3aec-115">**이름**</span><span class="sxs-lookup"><span data-stu-id="b3aec-115">**Name**</span></span>  
 <span data-ttu-id="b3aec-116">폴더 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-116">Specify the name of the folder.</span></span> <span data-ttu-id="b3aec-117">이름은 하나 이상의 영숫자 문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-117">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="b3aec-118">공백과 특정 기호도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-118">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="b3aec-119">이름을 지정할 때 ; ?</span><span class="sxs-lookup"><span data-stu-id="b3aec-119">Do not use the characters ; ?</span></span> <span data-ttu-id="b3aec-120">: \@ & = +, $/\* \< > | "로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-120">: \@ & = + , $ / \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="b3aec-121">**설명**</span><span class="sxs-lookup"><span data-stu-id="b3aec-121">**Description**</span></span>  
 <span data-ttu-id="b3aec-122">폴더 내용에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-122">Type a description of folder contents.</span></span> <span data-ttu-id="b3aec-123">이 설명은 해당 폴더 액세스 권한이 있는 사용자의 내용 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3aec-123">This description appears in the Contents page to users who have permission to access the folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3aec-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3aec-124">See Also</span></span>  
 <span data-ttu-id="b3aec-125">[폴더 &#40;보고서 관리자 만들기, 삭제 또는 수정&#41;](report-server/create-delete-or-modify-a-folder-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b3aec-125">[Create, Delete, or Modify a Folder &#40;Report Manager&#41;](report-server/create-delete-or-modify-a-folder-report-manager.md) </span></span>  
 <span data-ttu-id="b3aec-126">[일반 속성 페이지, 폴더 &#40;보고서 관리자&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b3aec-126">[General Properties Page, Folders &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span></span>  
 <span data-ttu-id="b3aec-127">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="b3aec-127">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="b3aec-128">[내용 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b3aec-128">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="b3aec-129">[F1 도움말 보고서 관리자](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="b3aec-129">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="b3aec-130">일반 속성 페이지, 폴더 &#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="b3aec-130">General Properties Page, Folders &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/general-properties-page-folders-report-manager.md)  
  
  
