---
title: Reporting Services 로그인 대화 상자(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 232ee51614a668b07263c3e3a4182f23652135bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736003"
---
# <a name="reporting-services-login-dialog-box-ssrs"></a><span data-ttu-id="22f5f-102">Reporting Services 로그인 대화 상자(SSRS)</span><span class="sxs-lookup"><span data-stu-id="22f5f-102">Reporting Services Login Dialog Box (SSRS)</span></span>
  <span data-ttu-id="22f5f-103">**Reporting Services 로그인** 대화 상자를 사용하여 보고서 서버에 보고서를 게시하는 데 사용할 자격 증명을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22f5f-103">Use the **Reporting Services Login** dialog box to provide credentials to publish reports to the report server.</span></span>  
  
-   <span data-ttu-id="22f5f-104">**참고** 프로젝트에 대한 **TargetServerURL** 배포 속성을 설정한 이후 보고서 서버에 보고서를 처음 게시한 경우에는 지정한 서버 이름이 `http://localhost/reportserver`가 아니라 `http://localhost/reports`와 비슷한 형태인지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="22f5f-104">**Note** If this is the first time you have published a report to a report server since set you set the deployment property **TargetServerURL** for a project, verify that the server name you specified is similar to `http://localhost/reportserver`, and not `http://localhost/reports`.</span></span> <span data-ttu-id="22f5f-105">로컬 서버에 `reports` 디렉터리 대신 `reportserver` 디렉터리를 지정할 경우 이 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="22f5f-105">Specifying the `reports` directory on the local server instead of the `reportserver` directory indirectly causes this dialog box to open.</span></span> <span data-ttu-id="22f5f-106">**TargetServerURL** 설정 방법에 대한 자세한 내용은 [배포 속성 설정&#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22f5f-106">For more information about setting **TargetServerURL**, see [Set Deployment Properties &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="22f5f-107">옵션</span><span class="sxs-lookup"><span data-stu-id="22f5f-107">Options</span></span>  
 <span data-ttu-id="22f5f-108">**Server**</span><span class="sxs-lookup"><span data-stu-id="22f5f-108">**Server**</span></span>  
 <span data-ttu-id="22f5f-109">보고서 서버의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="22f5f-109">Displays the name of the report server.</span></span> <span data-ttu-id="22f5f-110">예들 들어 `http://localhost/reportserver`입니다.</span><span class="sxs-lookup"><span data-stu-id="22f5f-110">For example, `http://localhost/reportserver`.</span></span> <span data-ttu-id="22f5f-111">기본 포트 80 이외의 다른 포트를 사용하는 보고서 서버의 경우 포트 번호를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22f5f-111">For report servers that use a different port than default port 80, include the port number.</span></span> <span data-ttu-id="22f5f-112">예들 들어 `http://localhost:81/reportserver`입니다.</span><span class="sxs-lookup"><span data-stu-id="22f5f-112">For example, `http://localhost:81/reportserver`.</span></span>  
  
 <span data-ttu-id="22f5f-113">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="22f5f-113">**User name**</span></span>  
 <span data-ttu-id="22f5f-114">웹 서비스에 로그인할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="22f5f-114">Type the user name to log in to the Web service.</span></span>  
  
 <span data-ttu-id="22f5f-115">**암호**</span><span class="sxs-lookup"><span data-stu-id="22f5f-115">**Password**</span></span>  
 <span data-ttu-id="22f5f-116">웹 서비스에 로그인할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="22f5f-116">Type the password to log in to the Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f5f-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22f5f-117">See Also</span></span>  
 <span data-ttu-id="22f5f-118">[Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="22f5f-118">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="22f5f-119">[보고서 데이터 원본에 대 한 자격 증명 및 연결 정보 지정](../report-data/specify-credential-and-connection-information-for-report-data-sources.md) [보고서 디자이너 F1 도움말](report-designer-f1-help.md)</span><span class="sxs-lookup"><span data-stu-id="22f5f-119">[Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Report Designer F1 Help](report-designer-f1-help.md)</span></span>  
  
  
