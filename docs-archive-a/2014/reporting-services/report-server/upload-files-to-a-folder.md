---
title: 폴더에 파일 업로드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
- files [Reporting Services]
- folders [Reporting Services], uploading files to
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cfb595ed6059436d17cb82262f5d1975a8397dbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650612"
---
# <a name="upload-files-to-a-folder"></a><span data-ttu-id="4f051-102">폴더에 파일 업로드</span><span class="sxs-lookup"><span data-stu-id="4f051-102">Upload Files to a Folder</span></span>
  <span data-ttu-id="4f051-103">파일 시스템에서 파일을 업로드하여 보고서 서버 데이터베이스에 관리되는 항목으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-103">You can upload files from the file system and store them as managed items in a report server database.</span></span> <span data-ttu-id="4f051-104">파일을 업로드할 때 발생하는 상황은 파일 형식에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-104">What happens when you upload a file depends on the file type.</span></span>

-   <span data-ttu-id="4f051-105">.rdl 파일을 업로드하는 것은 보고서를 게시하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-105">Uploading an .rdl file is equivalent to publishing a report.</span></span>

-   <span data-ttu-id="4f051-106">다른 파일을 업로드하면 보고서 서버 데이터베이스에 단일 이진 개체로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-106">Uploading any other file adds it to the report server database as a single binary object.</span></span> <span data-ttu-id="4f051-107">이 파일은 보고서 서버에 리소스로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-107">These files are published to a report server as a resource.</span></span> <span data-ttu-id="4f051-108">리소스는 어떤 파일 형식이든 상관없습니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-108">Resources can be any file type.</span></span> <span data-ttu-id="4f051-109">파일 확장명이 알려진 MIME 형식과 일치하면 해당 MIME 형식을 나타내는 아이콘이 리소스 형식을 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-109">If the file extension matches a known MIME type, an icon for that MIME type is used to identify the resource type.</span></span> <span data-ttu-id="4f051-110">그 밖의 일반 파일 아이콘은 리소스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-110">Otherwise, a generic file icon indicates a resource.</span></span>

> [!NOTE]
>  <span data-ttu-id="4f051-111">공유 데이터 원본을 만들 때는 보고서 데이터 원본 파일(.rds)을 업로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-111">You cannot upload a report data source (.rds) file to create a shared data source.</span></span> <span data-ttu-id="4f051-112">.rds 파일은 보고서 디자이너에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-112">An .rds file is used only in Report Designer.</span></span> <span data-ttu-id="4f051-113">이 파일은 보고서 관리자를 통해 정의하고 관리하는 공유 데이터 원본 항목에는 내용을 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-113">It cannot provide the content for a shared data source item that you define and manage through Report Manager.</span></span> <span data-ttu-id="4f051-114">데이터 원본을 업로드하는 대신 .rds 파일을 기반으로 공유 데이터 원본을 만드는 스크립트를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-114">As an alternative to uploading, you can write a script that creates a shared data source based on a .rds file.</span></span>

 <span data-ttu-id="4f051-115">업로드한 항목의 최대 파일 크기는 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-115">The maximum file size for uploaded items is determined by [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].</span></span> <span data-ttu-id="4f051-116">기본적으로 최대 크기는 4MB입니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-116">By default, the maximum size is 4 megabytes (MB).</span></span>

 <span data-ttu-id="4f051-117">보고서 서버 데이터베이스에 업로드한 파일은 폴더 계층에 다음 아이콘으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-117">Visually, files that you upload to a report server database are represented in the folder hierarchy with the following icons.</span></span>

 <span data-ttu-id="4f051-118">![보고서 아이콘](../media/hlp-16doc.gif "보고서 아이콘") 보고서 아이콘</span><span class="sxs-lookup"><span data-stu-id="4f051-118">![Report icon](../media/hlp-16doc.gif "Report icon") report icon</span></span>

 <span data-ttu-id="4f051-119">![모델 아이콘](../media/model-icon.gif "모델 아이콘") 보고서 모델 아이콘</span><span class="sxs-lookup"><span data-stu-id="4f051-119">![Model icon](../media/model-icon.gif "Model icon") report model icon</span></span>

 <span data-ttu-id="4f051-120">![일반 리소스 아이콘](../media/hlp-16file.gif "일반 리소스 아이콘") 일반 리소스 아이콘</span><span class="sxs-lookup"><span data-stu-id="4f051-120">![generic resource icon](../media/hlp-16file.gif "generic resource icon") generic resource icon</span></span>

 <span data-ttu-id="4f051-121">파일을 업로드하는 경우 파일은 항상 현재 선택된 폴더에 놓입니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-121">When you upload a file, it is always placed in the folder that is currently selected.</span></span> <span data-ttu-id="4f051-122">처음에 항목을 포함시킬 폴더로 이동하거나 파일을 업로드한 다음 나중에 최종 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-122">You can navigate to the folder that you want to contain the item first, or you can upload a file and then move it to a final location later.</span></span>

 <span data-ttu-id="4f051-123">파일을 업로드하려면 보고서 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-123">To upload a file, use Report Manager.</span></span> <span data-ttu-id="4f051-124">보고서 서버로 파일을 업로드할 수 있는지 여부는 사용자의 역할 할당에 속하는 태스크에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-124">Whether you can upload files to a report server depends on tasks that are part of your role assignment.</span></span> <span data-ttu-id="4f051-125">기본 보안을 사용할 경우 로컬 관리자는 보고서 서버에 항목을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-125">If you are using default security, local administrators can add items to a report server.</span></span> <span data-ttu-id="4f051-126">내 보고서를 설정한 경우 내 보고서 폴더를 갖고 있는 모든 사용자가 해당 폴더로 항목을 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-126">If My Reports is enabled, any user who has a My Reports folder has permission to upload items to that folder.</span></span> <span data-ttu-id="4f051-127">사용자 지정 역할 할당을 사용하는 경우 역할 할당에 폴더 관리 지원 태스크가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f051-127">If you use custom role assignments, the role assignment must include tasks that support folder management.</span></span>

|<span data-ttu-id="4f051-128">원하는 작업</span><span class="sxs-lookup"><span data-stu-id="4f051-128">To do this</span></span>|<span data-ttu-id="4f051-129">포함되는 태스크</span><span class="sxs-lookup"><span data-stu-id="4f051-129">Include these tasks</span></span>|
|----------------|-------------------------|
|<span data-ttu-id="4f051-130">폴더에 .rdl 파일 업로드</span><span class="sxs-lookup"><span data-stu-id="4f051-130">Upload an .rdl file to a folder</span></span>|<span data-ttu-id="4f051-131">보고서 관리</span><span class="sxs-lookup"><span data-stu-id="4f051-131">Manage reports</span></span>|
|<span data-ttu-id="4f051-132">파일을 이진 개체로 업로드</span><span class="sxs-lookup"><span data-stu-id="4f051-132">Upload any file as a binary object</span></span>|<span data-ttu-id="4f051-133">리소스 관리</span><span class="sxs-lookup"><span data-stu-id="4f051-133">Manage resources</span></span>|
|<span data-ttu-id="4f051-134">폴더의 내용 보기</span><span class="sxs-lookup"><span data-stu-id="4f051-134">View the contents of a folder</span></span>|<span data-ttu-id="4f051-135">리소스 보기, 보고서 보기</span><span class="sxs-lookup"><span data-stu-id="4f051-135">View resources, View reports</span></span>|

## <a name="see-also"></a><span data-ttu-id="4f051-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4f051-136">See Also</span></span>
 <span data-ttu-id="4f051-137">[보고서 관리자 &#40;SSRS 기본 모드&#41;].. /report-manager-ssrs-native-mode.md) [기본 모드 보고서 서버에 대 한 사용 권한 부여 보고서 서버](../security/granting-permissions-on-a-native-mode-report-server.md) [작업 및 사용 권한에](../security/tasks-and-permissions.md) [파일 또는 보고서 &#40;보고서 관리자 업로드&#41;](../reports/upload-a-file-or-report-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="4f051-137">[Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md) [Granting Permissions on a Native Mode Report Server](../security/granting-permissions-on-a-native-mode-report-server.md) [Tasks and Permissions](../security/tasks-and-permissions.md) [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md)</span></span>


