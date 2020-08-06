---
title: 파일 또는 보고서 업로드(보고서 관리자) | Microsoft Docs
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
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 119e2b22976dc227e017b81a59b698cf9eb7457f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648279"
---
# <a name="upload-a-file-or-report-report-manager"></a><span data-ttu-id="1ee75-102">파일 또는 보고서 업로드(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="1ee75-102">Upload a File or Report (Report Manager)</span></span>
  <span data-ttu-id="1ee75-103">보고서 관리자에서는 업로드 기능을 제공하므로 클라이언트 애플리케이션에서 보고서, 모델 및 기타 파일을 게시하지 않고도 이러한 항목을 보고서 서버에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-103">Report Manager provides an upload feature so that you can add reports, models, and other files to a report server without having to publish those items from a client application.</span></span> <span data-ttu-id="1ee75-104">파일 시스템에서 업로드한 파일은 보고서 서버에 항목으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-104">Files that you upload from the file system are stored as items on the report server.</span></span> <span data-ttu-id="1ee75-105">업로드한 파일 형식은 저장되는 방식에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-105">The type of file you upload determines how it is stored:</span></span>  
  
-   <span data-ttu-id="1ee75-106">.rdl 파일은 보고서로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-106">.rdl files are stored as reports.</span></span>  
  
-   <span data-ttu-id="1ee75-107">.smdl 파일은 보고서 모델로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-107">.smdl files are stored as report models.</span></span>  
  
-   <span data-ttu-id="1ee75-108">공유 데이터 원본 파일(.rds)을 비롯한 다른 모든 파일은 리소스로 업로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-108">All other files, including shared data source (.rds) files, are uploaded as resources.</span></span> <span data-ttu-id="1ee75-109">리소스는 보고서 서버에서 처리되지 않지만 보고서 서버가 MIME 형식의 파일을 지원하는 경우 보고서 관리자에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-109">Resources are not processed by a report server, but can be viewed in Report Manager if the report server supports the MIME type of the file.</span></span>  
  
### <a name="to-upload-a-file-or-report"></a><span data-ttu-id="1ee75-110">파일 또는 보고서를 업로드하려면</span><span class="sxs-lookup"><span data-stu-id="1ee75-110">To upload a file or report</span></span>  
  
1.  <span data-ttu-id="1ee75-111">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-111">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="1ee75-112">보고서 관리자에서 **내용** 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-112">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="1ee75-113">항목을 추가할 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-113">Navigate to the folder to which you want to add an item.</span></span>  
  
3.  <span data-ttu-id="1ee75-114">**파일 업로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-114">Click **Upload File**.</span></span>  
  
4.  <span data-ttu-id="1ee75-115">**찾아보기** 를 클릭하여 업로드할 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-115">Click **Browse** to select a file to upload.</span></span> <span data-ttu-id="1ee75-116">보고서 정의 파일, 이미지, 문서 등 보고서 서버에서 사용할 수 있는 모든 파일을 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-116">You can upload a report definition file, an image, a document, or any file that you want to make available on the report server.</span></span>  
  
5.  <span data-ttu-id="1ee75-117">새 항목의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-117">Type a name for the new item.</span></span> <span data-ttu-id="1ee75-118">항목 이름에 공백을 사용할 수 있지만 다음과 같은 예약 문자는 사용할 수 없습니다. ; ?</span><span class="sxs-lookup"><span data-stu-id="1ee75-118">An item name can include spaces, but cannot include the reserved characters: ; ?</span></span> <span data-ttu-id="1ee75-119">: \@ & = +, $/\* \< > |입니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-119">: \@ & = + , $ / \* \< > |.</span></span>  
  
6.  <span data-ttu-id="1ee75-120">기존 항목을 새 항목으로 바꾸려면 **항목이 있으면 덮어쓰기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ee75-120">If you want to replace an existing item with the new item, select **Overwrite item if it exists**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1ee75-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ee75-121">See Also</span></span>  
 <span data-ttu-id="1ee75-122">[공유 데이터 원본 &#40;보고서 관리자 만들기, 삭제 또는 수정&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1ee75-122">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 <span data-ttu-id="1ee75-123">[내용 페이지 &#40;보고서 관리자&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1ee75-123">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="1ee75-124">[파일 업로드 페이지 &#40;보고서 관리자&#41;](../upload-file-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1ee75-124">[Upload File Page &#40;Report Manager&#41;](../upload-file-page-report-manager.md) </span></span>  
 [<span data-ttu-id="1ee75-125">폴더에 파일 업로드</span><span class="sxs-lookup"><span data-stu-id="1ee75-125">Upload Files to a Folder</span></span>](../report-server/upload-files-to-a-folder.md)  
  
  
