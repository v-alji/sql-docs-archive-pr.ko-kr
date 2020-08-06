---
title: Azure Blob 다운로드 작업 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdltask.f1
- sql11.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e2f61260b1fceaad3c27a0ce6ab6af28b15582bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729715"
---
# <a name="azure-blob-download-task"></a><span data-ttu-id="1a80c-102">Azure Blob 다운로드 작업</span><span class="sxs-lookup"><span data-stu-id="1a80c-102">Azure Blob Download Task</span></span>
  <span data-ttu-id="1a80c-103">Azure Blob 다운로드 작업을 사용하면 SSIS 패키지에서 Azure Blob Storage의 파일을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-103">The Azure Blob Download Task enables an SSIS package to download files from an Azure blob storage.</span></span>   
<span data-ttu-id="1a80c-104">**Azure Blob 다운로드 태스크**를 추가하려면 이 작업을 SSIS 디자이너로 끌어서 놓고 두 번 클릭하거나 마우스 오른쪽 단추를 클릭하고 **편집** 을 클릭하여 다음과 같은 **Azure Blob 다운로드 태스크 편집기** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-104">To add an **Azure Blob Download Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure Blob Download Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="1a80c-105">다음 표에서는 이 대화 상자의 필드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-105">The following table provides description for the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a80c-106">**필드**</span><span class="sxs-lookup"><span data-stu-id="1a80c-106">**Field**</span></span>|<span data-ttu-id="1a80c-107">**설명**</span><span class="sxs-lookup"><span data-stu-id="1a80c-107">**Description**</span></span>|  
|<span data-ttu-id="1a80c-108">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="1a80c-108">AzureStorageConnection</span></span>|<span data-ttu-id="1a80c-109">기존 Azure Storage 연결 관리자를 지정하거나 Blob 파일이 호스트되는 위치를 가리키는 Azure Storage 계정을 참조하는 스토리지 연결 관리자를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-109">Specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account, which points to where the blob files are hosted.</span></span>|  
|<span data-ttu-id="1a80c-110">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="1a80c-110">BlobContainer</span></span>|<span data-ttu-id="1a80c-111">다운로드할 Blob 파일을 포함하는 Blob 컨테이너의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-111">Specifies the name of the blob container that contains the blob files to be downloaded.</span></span>|  
|<span data-ttu-id="1a80c-112">BlobDirectory</span><span class="sxs-lookup"><span data-stu-id="1a80c-112">BlobDirectory</span></span>|<span data-ttu-id="1a80c-113">다운로드할 Blob 파일을 포함하는 Blob 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-113">Specifies the blob directory that contains the blob files to be downloaded.</span></span> <span data-ttu-id="1a80c-114">blob 디렉터리는 가상 계층 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-114">The blob directory is a virtual hierarchical structure.</span></span>|  
|<span data-ttu-id="1a80c-115">LocalDirectory</span><span class="sxs-lookup"><span data-stu-id="1a80c-115">LocalDirectory</span></span>|<span data-ttu-id="1a80c-116">다운로드한 Blob 파일을 저장할 로컬 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-116">Specifies the local directory where the downloaded blob files will be stored.</span></span>|  
|<span data-ttu-id="1a80c-117">FileName</span><span class="sxs-lookup"><span data-stu-id="1a80c-117">FileName</span></span>|<span data-ttu-id="1a80c-118">지정된 이름 패턴의 파일을 선택할 이름 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-118">Specifies a name filter to select files with the specified name pattern.</span></span> <span data-ttu-id="1a80c-119">예를 들어</span><span class="sxs-lookup"><span data-stu-id="1a80c-119">E.g.</span></span> <span data-ttu-id="1a80c-120">MySheet\*.xls\* 는 MySheet001.xls 및 MySheetABC.xlsx와 같은 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-120">MySheet\*.xls\* includes files such as MySheet001.xls and MySheetABC.xlsx.</span></span>|  
|<span data-ttu-id="1a80c-121">TimeRangeFrom/TimeRangeTo</span><span class="sxs-lookup"><span data-stu-id="1a80c-121">TimeRangeFrom/TimeRangeTo</span></span>|<span data-ttu-id="1a80c-122">시간 범위 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-122">Specifies a time range filter.</span></span> <span data-ttu-id="1a80c-123">**TimeRangeFrom** 에서 **TimeRangeTo** 사이에 수정된 파일이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a80c-123">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be included.</span></span>|  
  
  
