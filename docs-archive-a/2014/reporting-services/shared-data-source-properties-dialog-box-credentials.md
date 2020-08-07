---
title: 공유 데이터 원본 속성 대화 상자, 자격 증명 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shareddatasource.credentials.f1
ms.assetid: c08d1a5f-206b-4d53-ab1a-368b651ee5bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8594c6627c033d31937b2aa8691869cdbba213b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732376"
---
# <a name="shared-data-source-properties-dialog-box-credentials"></a><span data-ttu-id="b7364-102">공유 데이터 원본 속성 대화 상자, 자격 증명</span><span class="sxs-lookup"><span data-stu-id="b7364-102">Shared Data Source Properties Dialog Box, Credentials</span></span>
  <span data-ttu-id="b7364-103">**공유 데이터 원본 속성** 대화 상자에서 **자격 증명** 을 선택하여 보고서의 공유 데이터 원본에 연결하는 데 필요한 자격 증명을 표시하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-103">Select **Credentials** on the **Shared Data Source Properties** dialog box to display and modify credentials to connect to a shared data source in the report.</span></span> <span data-ttu-id="b7364-104">사용자가 제공하는 자격 증명은 데이터 원본에 액세스하고 보고서를 미리 보기 위해 데이터의 복사본을 캐시하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-104">The credentials that you provide are used to access the data source and to cache a copy of the data for previewing reports.</span></span> <span data-ttu-id="b7364-105">미리 보기 데이터 캐시 방법에 대한 자세한 내용은 [보고서 미리 보기](reports/previewing-reports.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7364-105">For more information about how preview data is cached, see [Previewing Reports](reports/previewing-reports.md).</span></span> <span data-ttu-id="b7364-106">자격 증명에 대한 자세한 내용은 [보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](report-data/specify-credential-and-connection-information-for-report-data-sources.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7364-106">For more information about credentials, see [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b7364-107">옵션</span><span class="sxs-lookup"><span data-stu-id="b7364-107">Options</span></span>  
 <span data-ttu-id="b7364-108">**Windows 인증 사용(통합 보안)**</span><span class="sxs-lookup"><span data-stu-id="b7364-108">**Use Windows Authentication (integrated security)**</span></span>  
 <span data-ttu-id="b7364-109">Windows 인증을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-109">Select this option to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="b7364-110">**이 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="b7364-110">**Use this user name and password**</span></span>  
 <span data-ttu-id="b7364-111">특정 사용자 이름 및 암호를 제공하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-111">Select this option to provide a specific user name and password.</span></span> <span data-ttu-id="b7364-112">공유 데이터 원본의 경우 보고서 서버 프로젝트를 대상 서버에 게시하면 사용자 이름과 암호가 데이터베이스에 대해 저장된 자격 증명으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-112">For shared data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database.</span></span> <span data-ttu-id="b7364-113">사용자 이름과 암호를 Windows 자격 증명으로 사용하려는 경우 대상 서버에서 게시된 공유 데이터 원본에 대한 속성을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-113">If you want to use the user name and password as Windows credentials, you can edit the properties for the published shared data source on the target server.</span></span> <span data-ttu-id="b7364-114">자세한 내용은 [공유 데이터 원본 만들기, 삭제 또는 수정&#40;보고서 관리자&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7364-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md).</span></span>  
  
 <span data-ttu-id="b7364-115">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="b7364-115">**User name**</span></span>  
 <span data-ttu-id="b7364-116">데이터 원본에 로그인할 때 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-116">Type a user name to log in to the data source.</span></span>  
  
 <span data-ttu-id="b7364-117">**암호**</span><span class="sxs-lookup"><span data-stu-id="b7364-117">**Password**</span></span>  
 <span data-ttu-id="b7364-118">데이터 원본에 로그인할 때 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-118">Type a password to log in to the data source.</span></span>  
  
 <span data-ttu-id="b7364-119">**자격 증명 확인**</span><span class="sxs-lookup"><span data-stu-id="b7364-119">**Prompt for credentials**</span></span>  
 <span data-ttu-id="b7364-120">보고서 실행 시 자격 증명을 요청하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-120">Select this option to prompt for credentials when the report is run.</span></span>  
  
 <span data-ttu-id="b7364-121">**프롬프트 문자열 입력**</span><span class="sxs-lookup"><span data-stu-id="b7364-121">**Enter prompt string**</span></span>  
 <span data-ttu-id="b7364-122">데이터 원본에 대한 로그인 자격 증명을 제공하도록 사용자에게 표시할 메시지를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-122">Type a sentence to instruct the user to provide login credentials for the data source.</span></span>  
  
 <span data-ttu-id="b7364-123">**자격 증명 없음**</span><span class="sxs-lookup"><span data-stu-id="b7364-123">**No credentials**</span></span>  
 <span data-ttu-id="b7364-124">데이터 원본에 대해 자격 증명을 사용하지 않으려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-124">Select this option to provide no credentials for the data source.</span></span> <span data-ttu-id="b7364-125">이 옵션은 데이터 원본이 자격 증명을 허용하지 않거나 다른 방법으로 자격 증명을 전달하는 경우에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="b7364-125">This option only works if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7364-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b7364-126">See Also</span></span>  
 <span data-ttu-id="b7364-127">[Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="b7364-127">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="b7364-128">[보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="b7364-128">[Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span></span>  
 [<span data-ttu-id="b7364-129">공유 데이터 원본 속성 대화 상자, 일반</span><span class="sxs-lookup"><span data-stu-id="b7364-129">Shared Data Source Properties Dialog Box, General</span></span>](../../2014/reporting-services/shared-data-source-properties-dialog-box-general.md)  
  
  
