---
title: 패키지 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 85b7d512-0ea7-47f5-8937-b1af6592b5b5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c7a61d8c65c1934eb72101bf91ac3b73be60f94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743392"
---
# <a name="delete-packages"></a><span data-ttu-id="698c6-102">패키지 삭제</span><span class="sxs-lookup"><span data-stu-id="698c6-102">Delete Packages</span></span>
  <span data-ttu-id="698c6-103">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 파일 시스템에 저장된 패키지를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="698c6-103">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can delete packages saved to the file system.</span></span> <span data-ttu-id="698c6-104">패키지를 삭제하면 패키지가 영구적으로 삭제되어 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트로 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="698c6-104">If you delete a package, it is deleted permanently and it cannot be restored to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="698c6-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에서 제거한 패키지를 다른 프로젝트에서 사용하려면 **삭제** 옵션 대신 **프로젝트에서 제외** 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="698c6-105">If you want to remove packages from an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, but use them in other projects, then you should use the **Exclude From Project** option instead of the **Delete** option.</span></span>  
  
### <a name="to-delete-a-package-in-business-intelligence"></a><span data-ttu-id="698c6-106">Business Intelligence에서 패키지를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="698c6-106">To delete a package in Business Intelligence</span></span>  
  
1.  <span data-ttu-id="698c6-107">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 삭제할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="698c6-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to delete.</span></span>  
  
2.  <span data-ttu-id="698c6-108">솔루션 탐색기에서 패키지를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="698c6-108">In Solution Explorer, right-click the package, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="698c6-109">삭제를 확인하려면 **확인** 을 클릭하고 패키지를 유지하려면 **취소** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="698c6-109">Click **OK** to confirm the deletion or click **Cancel** to keep the package.</span></span>  
  
  
