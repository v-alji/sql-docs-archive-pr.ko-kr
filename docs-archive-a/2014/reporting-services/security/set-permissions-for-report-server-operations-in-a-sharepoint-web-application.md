---
title: SharePoint 웹 애플리케이션에서 보고서 서버 작업에 대한 사용 권한 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- SharePoint integration [Reporting Services], permissions
- SharePoint integration [Report Builder]
- security [Reporting Services], SharePoint integrated mode
- Report Builder 1.0, SharePoint integration
- model item security [Reporting Services]
ms.assetid: 9ea71f1a-ee9e-4337-95ff-d7cef79946e7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 68f503fef0e1350a502dd71c616fd309f0f30913
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739165"
---
# <a name="set-permissions-for-report-server-operations-in-a-sharepoint-web-application"></a>SharePoint 웹 애플리케이션에서 보고서 서버 작업에 대한 사용 권한 설정
  SharePoint 통합 모드로 실행되는 보고서 서버의 경우 SharePoint 사이트에 정의된 보안 설정에 따라 보고서, 보고서 모델 및 공유 데이터 원본을 보고 관리하는 방법이 결정됩니다. 기본 SharePoint 그룹, 사용 권한 수준 및 사용 권한 할당을 사용하는 경우 현재 보안 설정을 사용하여 보고서 및 기타 문서에 대해 작업을 수행할 수 있습니다.  
  
 기본 보안 설정으로 원하는 액세스 수준을 얻을 수 없는 경우 다음 섹션에 제공된 정보를 사용하여 특정 작업에 필요한 사용 권한을 확인할 수 있습니다.  
  
-   [보고서 보기 및 관리 권한](#permissionReports)  
  
-   [보고서 생성 및 보고서 작성기 사용 권한](#permissionReportBuilder)  
  
-   [공유 일정 생성 및 관리 권한](#permissionSharedSchedules)  
  
-   [구독 생성 및 관리 권한](#permissionSubscriptions)  
  
-   [공유 데이터 원본/보고서 모델 생성 및 관리 권한](#permissionDataSources)  
  
 SharePoint 사이트에서 대부분의 작업을 완료하는 데는 몇 가지 주요 사용 권한이 필요합니다. 이러한 사용 권한은 아래의 태스크 및 사용 권한 표에 나와 있지 않지만 사용자 지정 권한 수준을 만드는 경우에는 반드시 이를 포함시켜야 합니다.  
  
-   사용자 정보 찾아보기  
  
-   원격 인터페이스 사용  
  
-   열기  
  
-   애플리케이션 페이지 보기  
  
 미리 정의된 사용 권한 수준을 사용하고 있다면 위의 사용 권한이 모든 권한, 디자인, 참가, 읽기 및 제한된 액세스에 이미 포함되어 있으므로 아무런 동작도 수행할 필요가 없습니다. 그러나 사용자 지정 권한 수준을 사용하거나 특정 사용자 또는 그룹에 할당된 권한을 편집하는 경우 사용 권한을 직접 추가해야 합니다.  
  
 "사용자 정보 찾아보기" 권한이 있는 경우 보고서 서버는 항목의 작성자 및 항목을 마지막으로 수정한 사용자에 대한 정보를 반환할 수 있습니다. 이 사용 권한이 없는 경우 보고서 서버는 다음 오류를 반환합니다. 찾아보기 작업의 경우 "보고서 서버에 SharePoint 오류가 발생했습니다. ---> System.UnauthorizedAccessException: 액세스가 거부되었습니다."라는 오류가 반환됩니다. 게시 작업의 경우 "'<사용자 ' 사용자에 게 부여 된 권한으로는 \<domain> \\ \> 이 작업을 수행할 수 없습니다." 라는 오류 메시지가 나타납니다.  
  
##  <a name="permissions-for-viewing-and-managing-reports"></a><a name="permissionReports"></a> 보고서 보기 및 관리 권한  
 보고서 정의 권한은 보고서가 포함된 라이브러리의 목록 사용 권한을 통해 정의되지만 액세스를 제한하려는 경우 개별 보고서에 대해 사용 권한을 설정할 수 있습니다. 다음 표에서는 태스크 목록과 각 태스크를 지원하는 사용 권한을 설명합니다.  
  
|Task|사용 권한|  
|----------|----------------|  
|보고서 보기|파일이 포함된 라이브러리나 개별 보고서에 대한**항목 보기** 권한|  
|보고서 모델을 데이터 원본으로 사용하는 클릭 광고 보고서 보기|보고서 및 보고서 모델이 포함된 라이브러리나 개별 보고서 및 모델에 대한**항목 보기** 권한. 모델에 대한 보기 권한이 없는 경우 보고서를 열 수는 있지만 데이터에 대해 임시 탐색 작업을 수행할 수 없습니다.<br /><br /> 보고서 모델에서 모델 항목 보안을 사용하는 경우 사용자에게 보고서 모델에 대한 **사용 권한 열거** 권한도 있어야 합니다.|  
|보고서 기록의 스냅샷 보기|파일이 포함된 라이브러리나 개별 보고서에 대한**항목 편집** 권한. 일부 보고서의 경우 보고서 기록을 모두 보거나 하나도 보지 못할 수 있습니다. 보고서 기록의 개별 스냅샷에 대해서는 사용 권한을 설정할 수 없습니다.|  
|라이브러리에 보고서 업로드 또는 게시|보고서가 포함될 라이브러리에 대한**항목 추가** 권한|  
|데이터 원본 연결 정보, 처리 옵션 및 매개 변수 속성을 비롯한 보고서의 속성 설정|보고서가 포함된 라이브러리나 개별 보고서에 대한**항목 편집** 권한 공유 데이터 원본(.rsds)을 보고서에 사용하기 위해 선택하려면 해당 원본에 대한 보기 권한도 있어야 합니다.|  
|보고서 처리 예약|공유 일정을 선택하려면 보고서가 포함된 라이브러리가 있는 사이트에 대한 **열기** 권한이 있어야 합니다. 데이터 처리 또는 캐시 만료를 예약하려면 보고서가 포함된 라이브러리나 개별 보고서에 대한 **항목 편집** 권한이 있어야 합니다.|  
|보고서 삭제|보고서가 포함된 라이브러리나 개별 보고서에 대한**항목 삭제** 권한|  
|속성, 사용 권한, 기록 또는 구독에 영향을 주지 않고 보고서 정의를 최신 버전으로 바꾸기|보고서가 포함된 라이브러리나 개별 보고서에 대한**항목 편집** 권한|  
|보고서 기록에 스냅샷 만들기|보고서 기록을 만들려는 보고서가 포함된 라이브러리에 대한**항목 추가** 권한|  
|보고서 기록에 스냅샷 만들기|보고서 기록을 만들려는 보고서가 포함된 라이브러리에 대한**항목 추가** 권한|  
|보고서 기록의 스냅샷 삭제, 시간에 따라 체크 아웃 및 수정된 보고서 정의의 특정 버전 삭제|보고서 기록을 삭제하려는 보고서가 포함된 라이브러리에 대한**버전 삭제** 권한|  
|보고서 기록의 스냅샷 보기, 시간에 따라 체크 아웃 및 수정된 보고서 정의의 특정 버전 보기|보고서가 포함된 라이브러리에 대한**버전 보기** 권한|  
  
##  <a name="permissions-for-creating-reports-and-using-report-builder"></a><a name="permissionReportBuilder"></a> 보고서 생성 및 보고서 작성기 사용 권한  
 보고서 작성기는 임시 보고서를 만드는 데 사용할 수 있는 보고서 제작 도구입니다. 보고서 작성기는 보고서 모델을 데이터 원본으로 사용하여 임시 데이터 탐색 작업을 지원합니다. 보고서 작성기에서 모델을 로드하여 보고서를 생성 및 실행하고, 모델의 데이터를 클릭 광고하고, 필요에 따라 보고서를 라이브러리에 저장할 수 있습니다. 충분한 사용 권한이 있는 사용자는 이후에 동일한 보고서를 열고 임시 데이터 탐색 작업을 수행할 수도 있습니다.  
  
> [!NOTE]  
>  보고서 작성기에 대한 액세스 권한은 사용 권한 이외의 요인에 의해 결정될 수 있습니다. 사이트 관리자는 서버 속성을 설정하여 임시 보고 기능을 해제하거나 보고서 작성기 보고서 콘텐츠 형식을 추가하지 않아 보고서 작성기의 가용성을 제한할 수 있습니다. 이렇게 하면 사용자가 라이브러리의 **새로 만들기** 메뉴를 통해 새 보고서를 만들 수 없습니다. 또한 보고서 서버 관리자는 보고서 서버의 속성을 설정하여 보고서 작성기를 사용할 수 없게 만들 수 있습니다. 서버가 이러한 조건 중 하나에 해당되는 경우 필요한 사용 권한이 있어도 사용자가 보고서 작성기를 사용할 수 없습니다.  
  
 다음 표에서는 보고서를 만들고 보고서 작성기를 사용하기 위한 태스크 목록과 각 태스크를 지원하는 사용 권한을 설명합니다.  
  
|Task|사용 권한|  
|----------|----------------|  
|보고서 작성기 시작|보고서 작성기 사용 권한을 제어하기 위해 명시적으로 사용되는 권한은 없습니다. 보고서 서버 통합이 구성되어 있고 라이브러리에 항목을 추가할 권한이 사용자에게 있는 경우 보고서 작성기를 사용할 수 있습니다. 라이브러리의 **새로 만들기** 메뉴에서 보고서 작성기를 시작하려면 보고서 작성기 콘텐츠 형식을 등록해야 합니다. 자세한 내용은 [SharePoint 통합 모드&#41;에서 &#40;Reporting Services 라이브러리에 보고서 서버 콘텐츠 형식 추가 ](../add-reporting-services-content-types-to-a-sharepoint-library.md)를 참조 하세요.|  
|모델 또는 공유 데이터 원본 업로드|파일이 포함될 라이브러리에 대한**항목 추가** 권한|  
|모델 또는 종속 공유 데이터 원본 보기|파일이 포함된 라이브러리에 대한**항목 보기** 권한<br /><br /> 모델 항목 보안 설정이 모델에 포함되어 있는 경우 사용자에게 모델에 대한 **사용 권한 열거** 권한도 있어야 합니다.|  
|공유 데이터 원본에서 모델 생성|모델을 생성하는 데 사용할 공유 데이터 원본 파일(.rsds)이 포함된 라이브러리에 대한**항목 추가** 권한|  
|특정 모델 항목의 모델 내에 사용 권한 설정|라이브러리 및 보고서 모델 파일(.smdl)이 포함된 사이트에 대한**사용 권한 관리** 권한|  
|보고서 작성기에서 모델 로드|보고서 모델 파일(.smdl)에 대한**항목 편집** 권한|  
|보고서 작성기에서 보고서 정의 만들기, 라이브러리에 보고서 저장|라이브러리에 파일을 저장하기 위한**항목 추가** 권한|  
|보고서 작성기에서 보고서 편집|보고서 정의 파일에 대한**항목 편집** 권한|  
  
 구독 및 보고서 기록을 만들고 사용할 권한과 보고서 작성기 보고서에 대해 보고서 또는 데이터 처리 옵션을 설정할 권한은 표준 보고서 정의 파일에 대해 동일한 동작을 수행하는 데 사용되는 권한과 같습니다.  
  
##  <a name="permissions-for-creating-and-managing-shared-schedules"></a><a name="permissionSharedSchedules"></a> 공유 일정 생성 및 관리 권한  
 공유 일정은 라이브러리에 저장된 문서가 아닙니다. 따라서 이러한 일정을 만들고 관리하려면 사이트 사용 권한이 필요합니다. 특정 공유 일정에 대한 액세스 권한은 제한할 수 없습니다. 만드는 모든 공유 일정은 사이트 전반에서 열기 권한을 보유한 모든 사용자가 사용할 수 있습니다.  
  
 다음 표에서는 공유 일정을 만들고, 관리하고, 사용하기 위한 태스크 목록과 사용 권한을 설명합니다.  
  
|Task|사용 권한|  
|----------|----------------|  
|공유 일정 만들기, 편집 또는 삭제|사이트에 대한**웹 사이트 관리** 권한|  
|구독 처리 또는 데이터 검색을 위해 공유 일정 선택|라이브러리가 포함된 사이트에 대한**열기** 권한|  
  
##  <a name="permissions-for-creating-and-managing-subscriptions"></a><a name="permissionSubscriptions"></a> 구독 생성 및 관리 권한  
 SharePoint는 구독과 보기 권한 간에 종속성을 강제 적용합니다. 이에 따라 볼 권한이 없는 보고서는 구독할 수 없습니다. 보고서를 구독할 권한을 부여하면 자동으로 보기 권한이 부여됩니다.  
  
 다음 표에서는 구독을 만들고, 관리하고, 사용하기 위한 태스크 목록과 사용 권한을 설명합니다.  
  
|Task|사용 권한|  
|----------|----------------|  
|특정 보고서에 대한 사용자 소유의 구독 만들기, 편집 또는 삭제|보고서가 포함된 라이브러리나 보고서 자체에 대한**항목 편집** . 항목 보기는 종속된 사용 권한으로, 사용 권한 수준에 자동으로 포함됩니다. 구독을 만들 수 있는 사용자는 사용자 지정 일정을 만들어 해당 구독을 실행할 수도 있습니다.|  
|구독에 사용할 공유 일정 선택|라이브러리가 포함된 사이트에 대한**열기** 권한|  
|사이트 전반에서 구독 만들기, 편집 또는 삭제|사이트에 대한**알림 관리** 권한|  
  
##  <a name="permissions-for-creating-and-managing-shared-data-sources-and-report-models"></a><a name="permissionDataSources"></a> 공유 데이터 원본/보고서 모델 생성 및 관리 권한  
 공유 데이터 원본 파일(.rsds)에는 여러 보고서 및 모델에서 사용할 수 있는 데이터 원본 연결 정보가 포함되어 있습니다. 표준 보고서의 경우 .rsds 파일을 사용하여 데이터 원본 연결 정보를 지정하는 작업은 선택 사항입니다. 그러나 모델 기반 보고서의 경우에는 .rsds 파일을 반드시 사용해야 합니다. 보고서 모델은 항상 .rsds 파일을 사용하여 외부 데이터 원본에 연결합니다.  
  
 개별 사용자가 공유 데이터 원본을 보거나 관리할 수 있는지 여부를 결정하는 공유 데이터 원본의 속성을 설정할 수 있습니다. 공유 데이터 원본을 보거나 관리할 권한은 보고서 보기 권한과 다릅니다. .rsds 파일 자체에 대한 보기 권한이 없어도 .rsds 파일을 사용하는 보고서를 볼 수 있습니다.  
  
|작업|사용 권한|  
|-----------|----------------|  
|공유 데이터 원본 만들기|공유 데이터 원본이 포함된 라이브러리에 대한**항목 추가** 권한. 라이브러리의 새로 만들기 메뉴에서 새 공유 데이터 원본을 만들 수 있습니다. 이렇게 하려면 라이브러리에 보고서 데이터 원본 콘텐츠 형식을 등록해야 합니다. 자세한 내용은 [SharePoint 통합 모드&#41;에서 &#40;Reporting Services 라이브러리에 보고서 서버 콘텐츠 형식 추가 ](../add-reporting-services-content-types-to-a-sharepoint-library.md)를 참조 하세요.|  
|공유 데이터 원본 편집|공유 데이터 원본이 포함된 라이브러리나 공유 데이터 원본 자체에 대한**항목 편집** 권한|  
|공유 데이터 원본 삭제|공유 데이터 원본이 포함된 라이브러리나 공유 데이터 원본 자체에 대한**항목 삭제** 권한|  
|보고서에 공유 데이터 원본(.rsds) 사용|보고서나 보고서가 포함된 라이브러리에 대한**항목 편집** 권한. 공유 데이터 원본 선택은 보고서의 데이터 원본 속성을 설정하는 과정의 일부입니다.|  
|공유 데이터 원본에서 보고서 모델 생성|보고서 모델이 포함될 라이브러리에 대한**항목 추가** 권한|  
|보고서 모델 삭제|보고서 모델이 포함된 라이브러리나 보고서 모델 자체에 대한**항목 삭제** 권한|  
|특정 모델 항목의 모델 내에 사용 권한 설정|라이브러리 및 보고서 모델 파일(.smdl)이 포함된 사이트에 대한**사용 권한 관리** 권한|  
  
> [!NOTE]  
>  보고서 모델을 편집할 권한은 없습니다. 보고서 모델을 생성하거나 삭제할 수 있지만 SharePoint 사이트 내에서 편집할 수는 없습니다. 보고서 모델을 편집하려면 모델 디자이너가 필요합니다. 모델 디자이너는 SharePoint에서 설정한 사용 권한의 영향을 받지 않는 클라이언트 제작 도구입니다.  
  
## <a name="see-also"></a>참고 항목  
 [SharePoint 사이트의 보고서 서버 항목에 대한 사용 권한 부여](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Reporting Services의 역할 및 태스크와 SharePoint 그룹 및 사용 권한 비교](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)   
 [SharePoint 사이트의 보고서 서버 항목에 대한 사용 권한 부여](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [보고서 서버 항목에 대해 Windows SharePoint Services의 기본 제공 보안 사용](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md)  
  
  