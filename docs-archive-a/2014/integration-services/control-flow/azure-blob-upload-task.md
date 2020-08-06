---
title: Azure Blob 업로드 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobuptask.f1
- sql11.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ca15c5a77a2694293981121f4e5927be8ec0e1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729712"
---
# <a name="azure-blob-upload-task"></a><span data-ttu-id="8975b-102">Azure Blob 업로드 태스크</span><span class="sxs-lookup"><span data-stu-id="8975b-102">Azure Blob Upload Task</span></span>
  <span data-ttu-id="8975b-103">SSIS 패키지는 Azure Blob 업로드 태스크를 통해 Azure Blob 저장소에 파일을 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-103">The Azure Blob Upload Task enables an SSIS package to upload files to an Azure blob storage.</span></span>   
<span data-ttu-id="8975b-104">**Azure Blob 업로드 태스크**를 추가하려면 해당 태스크를 SSIS 디자이너로 끌어서 놓고 두 번 클릭하거나 마우스 오른쪽 단추를 클릭하고 **편집** 을 클릭하여 다음과 같은 **Azure Blob 업로드 태스크 편집기** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-104">To add an **Azure Blob Upload Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure Blob Upload Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="8975b-105">다음 표에서는 이 대화 상자의 필드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-105">The following table provides descriptions for the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8975b-106">**필드**</span><span class="sxs-lookup"><span data-stu-id="8975b-106">**Field**</span></span>|<span data-ttu-id="8975b-107">**설명**</span><span class="sxs-lookup"><span data-stu-id="8975b-107">**Description**</span></span>|  
|<span data-ttu-id="8975b-108">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="8975b-108">AzureStorageConnection</span></span>|<span data-ttu-id="8975b-109">기존 Azure Storage 연결 관리자를 지정하거나 Blob 파일이 호스트되는 위치를 가리키는 Azure Storage 계정을 참조하는 스토리지 연결 관리자를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-109">Specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account, which points to where the blob files are hosted.</span></span>|  
|<span data-ttu-id="8975b-110">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="8975b-110">BlobContainer</span></span>|<span data-ttu-id="8975b-111">blob으로 업로드된 파일이 저장되는 blob 컨테이너의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-111">Specifies the name of the blob container that will hold the uploaded files as blobs.</span></span>|  
|<span data-ttu-id="8975b-112">BlobDirectory</span><span class="sxs-lookup"><span data-stu-id="8975b-112">BlobDirectory</span></span>|<span data-ttu-id="8975b-113">업로드한 파일이 블록 blob으로 저장되는 blob 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-113">Specifies the blob directory where the uploaded file will be stored as a block blob.</span></span> <span data-ttu-id="8975b-114">blob 디렉터리는 가상 계층 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-114">The blob directory is a virtual hierarchical structure.</span></span> <span data-ttu-id="8975b-115">이미 있는 Blob은 업로드한 Blob으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-115">If the blob already exists, it will be replaced.</span></span>|  
|<span data-ttu-id="8975b-116">LocalDirectory</span><span class="sxs-lookup"><span data-stu-id="8975b-116">LocalDirectory</span></span>|<span data-ttu-id="8975b-117">업로드할 파일이 포함된 로컬 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-117">Specify the local directory that contains the files to be uploaded.</span></span>|  
|<span data-ttu-id="8975b-118">FileName</span><span class="sxs-lookup"><span data-stu-id="8975b-118">FileName</span></span>|<span data-ttu-id="8975b-119">지정된 이름 패턴의 파일을 선택할 이름 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-119">Specifies a name filter to select files with the specified name pattern.</span></span> <span data-ttu-id="8975b-120">예를 들어</span><span class="sxs-lookup"><span data-stu-id="8975b-120">E.g.</span></span> <span data-ttu-id="8975b-121">MySheet\*.xls\* 는 MySheet001.xls 및 MySheetABC.xlsx와 같은 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-121">MySheet\*.xls\* includes files such as MySheet001.xls and MySheetABC.xlsx.</span></span>|  
|<span data-ttu-id="8975b-122">TimeRangeFrom/TimeRangeTo</span><span class="sxs-lookup"><span data-stu-id="8975b-122">TimeRangeFrom/TimeRangeTo</span></span>|<span data-ttu-id="8975b-123">시간 범위 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-123">Specifies a time range filter.</span></span> <span data-ttu-id="8975b-124">**TimeRangeFrom** 에서 **TimeRangeTo** 사이에 수정된 파일이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8975b-124">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be included.</span></span>|  
  
  
