---
title: 리소스 업데이트(보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- updating resources
- resources [Reporting Services], updating
ms.assetid: d21f7493-bcf7-4e9e-9886-55ebdc1f1037
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0fca59e476c2820b715ff46729784edc562f74d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650613"
---
# <a name="update-a-resource-report-manager"></a><span data-ttu-id="b6452-102">리소스 업데이트(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="b6452-102">Update a Resource (Report Manager)</span></span>
  <span data-ttu-id="b6452-103">리소스를 최신 버전으로 바꾸어 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-103">You can update a resource by replacing it with a newer version.</span></span> <span data-ttu-id="b6452-104">리소스는 보고서 서버에 저장된 항목이며 사용자가 업로드한 파일의 내용을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-104">Resources are items stored on a report server that contain content from a file that you upload.</span></span> <span data-ttu-id="b6452-105">새롭거나 다른 파일 내용을 기존 리소스에 가져와 기존 리소스를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-105">You can replace an existing resource by importing new or different file content into the existing resource.</span></span> <span data-ttu-id="b6452-106">리소스를 업데이트하면 리소스에 대한 기존 속성과 보안 설정을 유지하면서 내용을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-106">Updating a resource provides a way to update content while preserving existing properties and security settings on the resource.</span></span>  
  
### <a name="to-update-a-resource"></a><span data-ttu-id="b6452-107">리소스를 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="b6452-107">To update a resource</span></span>  
  
1.  <span data-ttu-id="b6452-108">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-108">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="b6452-109">보고서 관리자에서 업데이트할 리소스로 이동하거나 해당 리소스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-109">In Report Manager, navigate to or search for the resource you want to update.</span></span>  
  
3.  <span data-ttu-id="b6452-110">리소스를 클릭하여 **보기** 페이지에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-110">Click the resource to open it in the **View** page.</span></span>  
  
4.  <span data-ttu-id="b6452-111">**속성** 을 클릭하여 **일반** 속성 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-111">Click **Properties** to open the **General** properties page.</span></span>  
  
5.  <span data-ttu-id="b6452-112">**바꾸기** 를 클릭하여 **리소스 가져오기** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-112">Click **Replace** to open the **Import Resource** page.</span></span>  
  
6.  <span data-ttu-id="b6452-113">**찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-113">Click **Browse**.</span></span>  
  
7.  <span data-ttu-id="b6452-114">현재 리소스를 바꾸는 데 사용할 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-114">Select the file that you want to use to replace the current resource.</span></span> <span data-ttu-id="b6452-115">리소스 파일의 업데이트 버전을 사용하거나 이름 또는 유형이 다른 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-115">You can use an updated version of the resource file, or specify a file with a different name or file type.</span></span>  
  
8.  <span data-ttu-id="b6452-116">**확인** 을 클릭하여 리소스 파일을 업로드하고 **리소스 가져오기** 페이지를 닫은 후 보고서 서버에 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-116">Click **OK** to upload the resource file, close the **Import Resource** page, and save your changes to the report server.</span></span>  
  
 <span data-ttu-id="b6452-117">업데이트하는 리소스가 보고서에 사용된 이미지를 포함하는 경우 업데이트된 이미지를 보려면 보고서를 새로 고쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6452-117">If the resource you are updating contains an image that is used in a report, you need to refresh the report to see the updated image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6452-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6452-118">See Also</span></span>  
 <span data-ttu-id="b6452-119">[내용 페이지 &#40;보고서 관리자&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b6452-119">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="b6452-120">[파일 업로드 페이지 &#40;보고서 관리자&#41;](../upload-file-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b6452-120">[Upload File Page &#40;Report Manager&#41;](../upload-file-page-report-manager.md) </span></span>  
 <span data-ttu-id="b6452-121">[폴더에 파일 업로드](upload-files-to-a-folder.md) </span><span class="sxs-lookup"><span data-stu-id="b6452-121">[Upload Files to a Folder](upload-files-to-a-folder.md) </span></span>  
 [<span data-ttu-id="b6452-122">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="b6452-122">Report Manager F1 Help</span></span>](../report-manager-f1-help.md)  
  
  
