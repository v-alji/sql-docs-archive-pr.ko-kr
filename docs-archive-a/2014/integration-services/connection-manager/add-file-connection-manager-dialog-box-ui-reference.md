---
title: 파일 연결 관리자 추가 대화 상자 UI 참조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnection.f1
helpviewer_keywords:
- Add File Connection Manager
ms.assetid: 9370bfb5-5993-4ad8-a9cd-2de53f320f34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 044d8e2eaae9db17d7155cb354f8d009750f44d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738578"
---
# <a name="add-file-connection-manager-dialog-box-ui-reference"></a><span data-ttu-id="7435c-102">파일 연결 관리자 추가 대화 상자 UI 참조</span><span class="sxs-lookup"><span data-stu-id="7435c-102">Add File Connection Manager Dialog Box UI Reference</span></span>
  <span data-ttu-id="7435c-103">**파일 연결 관리자 추가** 대화 상자를 사용하여 파일 또는 폴더 그룹에 대한 연결을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-103">Use the **Add File Connection Manager** dialog box to define a connection to a group of files or folders.</span></span>  
  
 <span data-ttu-id="7435c-104">다중 파일 연결 관리자에 대한 자세한 내용은 [Multiple Files Connection Manager](multiple-files-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7435c-104">To learn more about the Multiple Files connection manager, see [Multiple Files Connection Manager](multiple-files-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7435c-105">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 의 기본 제공 태스크 및 데이터 흐름 구성 요소는 다중 파일 연결 관리자를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-105">The built-in tasks and data flow components in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not use the Multiple Files connection manager.</span></span> <span data-ttu-id="7435c-106">그러나 스크립트 태스크와 스크립트 구성 요소에서 이 연결 관리자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-106">However, you can use this connection manager in the Script task or Script component.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7435c-107">옵션</span><span class="sxs-lookup"><span data-stu-id="7435c-107">Options</span></span>  
 <span data-ttu-id="7435c-108">**사용 유형**</span><span class="sxs-lookup"><span data-stu-id="7435c-108">**Usage type**</span></span>  
 <span data-ttu-id="7435c-109">다중 파일 연결 관리자에 사용할 파일 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-109">Specify the type of files to use for the multiple files connection manager.</span></span>  
  
|<span data-ttu-id="7435c-110">값</span><span class="sxs-lookup"><span data-stu-id="7435c-110">Value</span></span>|<span data-ttu-id="7435c-111">Description</span><span class="sxs-lookup"><span data-stu-id="7435c-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7435c-112">**파일 만들기**</span><span class="sxs-lookup"><span data-stu-id="7435c-112">**Create files**</span></span>|<span data-ttu-id="7435c-113">연결 관리자에서 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-113">The connection manager will create the files.</span></span>|  
|<span data-ttu-id="7435c-114">**기존 파일**</span><span class="sxs-lookup"><span data-stu-id="7435c-114">**Existing files**</span></span>|<span data-ttu-id="7435c-115">연결 관리자에서 기존 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-115">The connection manager will use existing files.</span></span>|  
|<span data-ttu-id="7435c-116">**폴더 만들기**</span><span class="sxs-lookup"><span data-stu-id="7435c-116">**Create folders**</span></span>|<span data-ttu-id="7435c-117">연결 관리자에서 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-117">The connection manager will create the folders.</span></span>|  
|<span data-ttu-id="7435c-118">**기존 폴더**</span><span class="sxs-lookup"><span data-stu-id="7435c-118">**Existing folders**</span></span>|<span data-ttu-id="7435c-119">연결 관리자에서 기존 폴더를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-119">The connection manager will use existing folders.</span></span>|  
  
 <span data-ttu-id="7435c-120">**파일/폴더**</span><span class="sxs-lookup"><span data-stu-id="7435c-120">**Files / Folders**</span></span>  
 <span data-ttu-id="7435c-121">다음과 같이 설명된 단추를 사용하여 추가한 파일이나 폴더를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-121">View the files or folders that you have added by using the buttons described as follows.</span></span>  
  
 <span data-ttu-id="7435c-122">**추가**</span><span class="sxs-lookup"><span data-stu-id="7435c-122">**Add**</span></span>  
 <span data-ttu-id="7435c-123">**파일 선택** 대화 상자를 사용하여 파일을 추가하거나 **폴더 찾아보기** 대화 상자를 사용하여 폴더를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-123">Add a file by using the **Select Files** dialog box, or add a folder by using the **Browse for Folder** dialog box.</span></span>  
  
 <span data-ttu-id="7435c-124">**편집**</span><span class="sxs-lookup"><span data-stu-id="7435c-124">**Edit**</span></span>  
 <span data-ttu-id="7435c-125">파일이나 폴더를 선택한 다음 **파일 선택** 또는 **폴더 찾아보기** 대화 상자를 사용하여 다른 파일이나 폴더로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-125">Select a file or folder, and then replace it with a different file or folder by using the **Select Files** or **Browse for Folder** dialog box.</span></span>  
  
 <span data-ttu-id="7435c-126">**제거**</span><span class="sxs-lookup"><span data-stu-id="7435c-126">**Remove**</span></span>  
 <span data-ttu-id="7435c-127">파일이나 폴더를 선택한 다음 **제거** 단추를 사용하여 목록에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-127">Select a file or folder, and then remove it from the list by using the **Remove** button.</span></span>  
  
 <span data-ttu-id="7435c-128">**화살표 단추**</span><span class="sxs-lookup"><span data-stu-id="7435c-128">**Arrow buttons**</span></span>  
 <span data-ttu-id="7435c-129">파일이나 폴더를 선택한 다음 화살표 단추를 통해 위/아래로 이동하여 액세스 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7435c-129">Select a file or folder, and then use the arrow buttons to move it up or down to specify the sequence of access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7435c-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7435c-130">See Also</span></span>  
 [<span data-ttu-id="7435c-131">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="7435c-131">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
  
  
