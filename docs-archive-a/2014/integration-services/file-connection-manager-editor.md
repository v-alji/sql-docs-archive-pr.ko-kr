---
title: 파일 연결 관리자 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnectionmanager.f1
helpviewer_keywords:
- File Connection Manager Editor
ms.assetid: 051c48e5-3d86-49af-b554-ff62e3de3622
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2f3261b836d4800787fc078b05b15e469d3c200d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659525"
---
# <a name="file-connection-manager-editor"></a><span data-ttu-id="c60aa-102">파일 연결 관리자 편집기</span><span class="sxs-lookup"><span data-stu-id="c60aa-102">File Connection Manager Editor</span></span>
  <span data-ttu-id="c60aa-103">**파일 연결 관리자 편집기** 대화 상자를 사용하여 파일이나 폴더에 연결할 때 사용할 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c60aa-103">Use the **File Connection Manager Editor** dialog box to specify the properties used to connect to a file or a folder.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c60aa-104">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 속성 창에 식을 지정하여 파일 연결 관리자에 대한 ConnectionString 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c60aa-104">You can set the ConnectionString property for the File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="c60aa-105">그러나 식을 사용하여 파일 또는 폴더를 지정할 때 유효성 검사 오류가 발생하지 않도록 하려면 **파일 연결 관리자 편집기**에서 **파일/폴더**에 대해 파일 또는 폴더 경로를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c60aa-105">However, to avoid a validation error when you use an expression to specify the file or folder, in the **File Connection Manager Editor**, for **File/Folder**, add a file or folder path.</span></span>  
  
 <span data-ttu-id="c60aa-106">파일 연결 관리자에 대한 자세한 내용은 [File Connection Manager](connection-manager/file-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c60aa-106">To learn more about the File connection manager, see [File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c60aa-107">옵션</span><span class="sxs-lookup"><span data-stu-id="c60aa-107">Options</span></span>  
 <span data-ttu-id="c60aa-108">**사용 유형**</span><span class="sxs-lookup"><span data-stu-id="c60aa-108">**Usage Type**</span></span>  
 <span data-ttu-id="c60aa-109">**파일 연결 관리자** 가 기존 파일 또는 폴더에 연결하는지 또는 새 파일 또는 폴더에 연결하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c60aa-109">Specify whether the **File Connection Manager** connects to an existing file or folder or creates a new file or folder.</span></span>  
  
|<span data-ttu-id="c60aa-110">값</span><span class="sxs-lookup"><span data-stu-id="c60aa-110">Value</span></span>|<span data-ttu-id="c60aa-111">Description</span><span class="sxs-lookup"><span data-stu-id="c60aa-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c60aa-112">파일 만들기</span><span class="sxs-lookup"><span data-stu-id="c60aa-112">Create file</span></span>|<span data-ttu-id="c60aa-113">런타임에 새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c60aa-113">Create a new file at run time.</span></span>|  
|<span data-ttu-id="c60aa-114">기존 파일</span><span class="sxs-lookup"><span data-stu-id="c60aa-114">Existing file</span></span>|<span data-ttu-id="c60aa-115">기존 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c60aa-115">Use an existing file.</span></span>|  
|<span data-ttu-id="c60aa-116">폴더 만들기</span><span class="sxs-lookup"><span data-stu-id="c60aa-116">Create folder</span></span>|<span data-ttu-id="c60aa-117">런타임에 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c60aa-117">Create a new folder at run time.</span></span>|  
|<span data-ttu-id="c60aa-118">기존 폴더</span><span class="sxs-lookup"><span data-stu-id="c60aa-118">Existing folder</span></span>|<span data-ttu-id="c60aa-119">기존 폴더를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c60aa-119">Use an existing folder.</span></span>|  
  
 <span data-ttu-id="c60aa-120">**파일/폴더**</span><span class="sxs-lookup"><span data-stu-id="c60aa-120">**File / Folder**</span></span>  
 <span data-ttu-id="c60aa-121">**파일**을 선택한 경우 사용할 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c60aa-121">If **File**, specify the file to use.</span></span>  
  
 <span data-ttu-id="c60aa-122">**폴더**를 선택한 경우 사용할 폴더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c60aa-122">If **Folder**, specify the folder to use.</span></span>  
  
 <span data-ttu-id="c60aa-123">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="c60aa-123">**Browse**</span></span>  
 <span data-ttu-id="c60aa-124">**파일 선택** 이나 **폴더 찾아보기** 대화 상자를 사용하여 파일이나 폴더를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c60aa-124">Select the file or folder by using the **Select File** or **Browse for Folder** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c60aa-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c60aa-125">See Also</span></span>  
 [<span data-ttu-id="c60aa-126">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="c60aa-126">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
