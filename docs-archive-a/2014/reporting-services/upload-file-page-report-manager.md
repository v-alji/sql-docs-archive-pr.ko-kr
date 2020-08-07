---
title: 파일 업로드 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7bb3166f-9374-4449-b66a-ffb77298507d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: de03c6c6bd03cbe083d5e1edfd320264d2cc3bde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734912"
---
# <a name="upload-file-page-report-manager"></a><span data-ttu-id="dd937-102">파일 업로드 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="dd937-102">Upload File Page (Report Manager)</span></span>
  <span data-ttu-id="dd937-103">파일 업로드 페이지를 사용하여 파일을 파일 시스템에서 보고서 서버 데이터베이스로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-103">Use the Upload File page to publish a file from the file system into the report server database.</span></span> <span data-ttu-id="dd937-104">업로드된 파일은 보고서 서버 폴더 계층 구조의 항목으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-104">Uploaded files are represented as items in the report server folder hierarchy.</span></span>  
  
-   <span data-ttu-id="dd937-105">업로드된 .rdl 파일은 보고서 서버에 보고서로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-105">Uploaded .rdl files are published to a report server as reports.</span></span>  
  
-   <span data-ttu-id="dd937-106">Uploaded .smdl 파일이 데이터 원본 뷰 정보를 포함하는 경우 이 파일은 보고서 모델로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-106">Uploaded .smdl files are published as report models if they contain data source view information.</span></span> <span data-ttu-id="dd937-107">데이터 원본 뷰 참조가 유실되면 업로드 중에 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-107">If they are missing a data source view reference, an error occurs during the upload.</span></span> <span data-ttu-id="dd937-108">[!INCLUDE[msCoName](../includes/msconame-md.md)]보고서 모델 프로젝트에서 smdl 파일을 업로드 하는 경우 데이터 원본 뷰 정보가 누락 될 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dd937-108">Data source view information might be missing if you upload an .smdl file from a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] report model project.</span></span> <span data-ttu-id="dd937-109">보고서 모델 프로젝트에서 데이터 원본 뷰 정보는 .smdl 파일 자체가 아닌 별도의 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-109">In report model projects, data source view information is stored in a separate file rather than in the .smdl file itself.</span></span>  
  
     <span data-ttu-id="dd937-110">데이터 원본 뷰 정보가 들어 있고 따라서 성공적으로 업로드할 수 있는 모델 파일은 이전에 보고서 서버에 게시된 후 서버에서 파일 시스템의 파일로 저장된 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-110">Model files that do contain data source view information (and can therefore be successfully uploaded) are those that have been previously published to a report server and then saved from the server to a file on the file system.</span></span> <span data-ttu-id="dd937-111">모델의 일반 속성 페이지를 열고 **편집** 을 클릭하여 모델을 연 경우 파일에 모델을 저장하고 보고서 서버에 새 모델로 해당 파일을 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-111">If you open the General Properties page of a model and click **Edit** to open the model, you can save it to a file and then upload it as a new model on the report server.</span></span> <span data-ttu-id="dd937-112">나중에 업로드하는 .smdl 파일은 모델 게시에 필요한 모든 정보를 포함하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-112">The .smdl file that you subsequently upload will have all of information that is necessary for model publication.</span></span>  
  
-   <span data-ttu-id="dd937-113">다른 모든 업로드한 파일 형식은 리소스로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-113">All other file types that you upload are stored as resources.</span></span> <span data-ttu-id="dd937-114">여기에는 보고서 데이터 원본 연결 정보가 있는 .rds 파일이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-114">This includes .rds files that contain report data source connection information.</span></span> <span data-ttu-id="dd937-115">.rds 파일을 업로드해도 보고서 서버에 공유 데이터 원본 항목이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-115">Uploading an .rds file does not produce a shared data source item on the report server.</span></span>  
  
 <span data-ttu-id="dd937-116">항목을 업로드하면 이 항목은 현재 폴더에 놓입니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-116">When you upload an item, it is placed in the current folder.</span></span> <span data-ttu-id="dd937-117">업로드가 완료된 후 항목을 다른 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-117">After the upload is complete, you can move the item to a different location.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd937-118">이 기능은 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-118">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dd937-119">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dd937-119">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="dd937-120">탐색</span><span class="sxs-lookup"><span data-stu-id="dd937-120">Navigation</span></span>  
 <span data-ttu-id="dd937-121">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="dd937-121">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-upload-file-page"></a><span data-ttu-id="dd937-122">파일 업로드 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="dd937-122">To open the Upload File page</span></span>  
  
1.  <span data-ttu-id="dd937-123">보고서 관리자를 열고 파일을 업로드할 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-123">Open Report Manager, and navigate to the folder in which you want to upload a file.</span></span>  
  
2.  <span data-ttu-id="dd937-124">도구 모음에서 **파일 업로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-124">In the toolbar, click **Upload File**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dd937-125">옵션</span><span class="sxs-lookup"><span data-stu-id="dd937-125">Options</span></span>  
 <span data-ttu-id="dd937-126">**업로드할 파일**</span><span class="sxs-lookup"><span data-stu-id="dd937-126">**File to Upload**</span></span>  
 <span data-ttu-id="dd937-127">파일 시스템에서 복사할 파일의 정규화된 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-127">Displays the fully qualified path to the file you are copying from the file system.</span></span>  
  
 <span data-ttu-id="dd937-128">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="dd937-128">**Browse**</span></span>  
 <span data-ttu-id="dd937-129">파일 시스템에서 파일을 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-129">Click to choose a file from the file system.</span></span>  
  
 <span data-ttu-id="dd937-130">**이름**</span><span class="sxs-lookup"><span data-stu-id="dd937-130">**Name**</span></span>  
 <span data-ttu-id="dd937-131">보고서 서버 네임스페이스에 표시될 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-131">Type the name of the file, as it will appear in the report server namespace.</span></span> <span data-ttu-id="dd937-132">이름은 하나 이상의 영숫자 문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-132">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="dd937-133">공백과 특정 기호도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-133">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="dd937-134">이름을 지정할 때 ; ?</span><span class="sxs-lookup"><span data-stu-id="dd937-134">Do not use the characters ; ?</span></span> <span data-ttu-id="dd937-135">: \@ & = +, $ \* \< > | "또는/로 항목 이름을 지정할 때</span><span class="sxs-lookup"><span data-stu-id="dd937-135">: \@ & = + , $ \* \< > | " or / when specifying an item name.</span></span>  
  
 <span data-ttu-id="dd937-136">**항목이 있으면 덮어쓰기**</span><span class="sxs-lookup"><span data-stu-id="dd937-136">**Overwrite item if it exists**</span></span>  
 <span data-ttu-id="dd937-137">기존 항목을 새 버전으로 교체하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-137">Select this check box if you want to replace an existing item with a newer version.</span></span> <span data-ttu-id="dd937-138">기존 버전을 덮어쓰려면 새 항목과 기존 항목의 이름이 정확히 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd937-138">To overwrite an existing version, the name of the new item and the existing item must be an exact match.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd937-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd937-139">See Also</span></span>  
 <span data-ttu-id="dd937-140">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="dd937-140">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="dd937-141">[내용 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="dd937-141">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="dd937-142">[F1 도움말 보고서 관리자](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="dd937-142">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="dd937-143">폴더에 파일 업로드</span><span class="sxs-lookup"><span data-stu-id="dd937-143">Upload Files to a Folder</span></span>](report-server/upload-files-to-a-folder.md)  
  
  
