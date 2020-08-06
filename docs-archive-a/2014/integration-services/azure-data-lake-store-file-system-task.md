---
title: Azure Data Lake Store 파일 시스템 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1bc37e774c5346190635e50259deb47f2f22a054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652293"
---
# <a name="azure-data-lake-store-file-system-task"></a><span data-ttu-id="ac5e5-102">Azure Data Lake Store 파일 시스템 태스크</span><span class="sxs-lookup"><span data-stu-id="ac5e5-102">Azure Data Lake Store File System Task</span></span>

<span data-ttu-id="ac5e5-103">사용자는 **Azure Data Lake Store 파일 시스템 태스크** 를 사용 하 여 [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/)에서 다양 한 파일 시스템 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-103">The **Azure Data Lake Store File System Task** enables users to perform various file system operations on [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).</span></span>

<span data-ttu-id="ac5e5-104">패키지에 Azure Data Lake Store 파일 시스템 태스크를 추가하려면 SSIS 도구 상자에서 디자이너 캔버스로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-104">To add an Azure Data Lake Store File System Task to a package, drag it from SSIS Toolbox to the designer canvas.</span></span> <span data-ttu-id="ac5e5-105">그런 다음 태스크를 두 번 클릭 하거나 태스크를 마우스 오른쪽 단추로 클릭 하 고 **편집**을 선택 하 여 태스크 편집기 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-105">Then double-click the task, or right-click the task and select **Edit**, to open the task editor dialog box.</span></span>

<span data-ttu-id="ac5e5-106">**작업** 속성은 수행할 파일 시스템 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-106">The **Operation** property specifies the file system operation to perform.</span></span> <span data-ttu-id="ac5e5-107">다음 작업이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-107">The following operations are supported.</span></span>

* <span data-ttu-id="ac5e5-108">**CopyToADLS:** ADLS에 파일을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-108">**CopyToADLS:** Upload files to ADLS.</span></span>
* <span data-ttu-id="ac5e5-109">**CopyFromADLS:** ADLS에서 파일을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-109">**CopyFromADLS:** Download files from ADLS.</span></span>

<span data-ttu-id="ac5e5-110">모든 작업의 경우 Azure Data Lake 연결 관리자를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-110">For any operation, you have to specify an Azure Data Lake connection manager.</span></span>

<span data-ttu-id="ac5e5-111">각 작업과 관련 된 속성에 대 한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-111">Here are the descriptions of the properties specific to each operation.</span></span>

## <a name="copytoadls"></a><span data-ttu-id="ac5e5-112">CopyToADLS</span><span class="sxs-lookup"><span data-stu-id="ac5e5-112">CopyToADLS</span></span>

* <span data-ttu-id="ac5e5-113">**Localdirectory:** 업로드할 파일이 포함 된 원본 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-113">**LocalDirectory:** Specifies the source directory which contains files to upload.</span></span>
* <span data-ttu-id="ac5e5-114">**FileNamePattern:** 원본 파일에 대한 파일 이름 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-114">**FileNamePattern:** Specifies a file name filter for source files.</span></span> <span data-ttu-id="ac5e5-115">지정 된 패턴과 일치 하는 이름을 가진 파일만 업로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-115">Only files whose name matches the specified pattern will be uploaded.</span></span> <span data-ttu-id="ac5e5-116">와일드카드 `*` 및 `?`가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-116">Wildcards `*` and `?` are supported.</span></span>
* <span data-ttu-id="ac5e5-117">**SearchRecursively:** 업로드할 파일에 대한 원본 디렉터리 내에서 재귀적으로 검색할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-117">**SearchRecursively:** Specifies whether to search recursively within the source directory for files to upload.</span></span>
* <span data-ttu-id="ac5e5-118">**AzureDataLakeDirectory:** 파일을 업로드할 ADLS 대상 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-118">**AzureDataLakeDirectory:** Specifies the ADLS destination directory to upload files to.</span></span>
* <span data-ttu-id="ac5e5-119">**Fileexpiry:** ADLS에 업로드 된 파일의 만료 날짜 및 시간을 지정 하거나이 속성을 비워 두어 파일이 만료 되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-119">**FileExpiry:** Specifies an expiration date and time for the files uploaded to ADLS, or leave this property blank to indicate that the files never expire.</span></span>

## <a name="copyfromadls"></a><span data-ttu-id="ac5e5-120">CopyFromADLS</span><span class="sxs-lookup"><span data-stu-id="ac5e5-120">CopyFromADLS</span></span>

* <span data-ttu-id="ac5e5-121">**AzureDataLakeDirectory:** 다운로드할 파일을 포함하는 ADLS 소스 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-121">**AzureDataLakeDirectory:** Specifies the ADLS source directory which contains the files to download.</span></span>
* <span data-ttu-id="ac5e5-122">**SearchRecursively:** 다운로드할 파일에 대한 원본 디렉터리 내에서 재귀적으로 검색할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-122">**SearchRecursively:** Specifies whether to search recursively within the source directory for files to download.</span></span>
* <span data-ttu-id="ac5e5-123">**LocalDirectory:** 다운로드한 파일을 저장할 대상 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5e5-123">**LocalDirectory:** Specifies the destination directory to store downloaded files.</span></span>
