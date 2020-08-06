---
title: DQSInstaller.exe를 사용하여 DQS 기술 자료 내보내기 및 가져오기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8234c63b-a018-4e55-8184-9a6bdf03274d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 64a8feb7bfded742da7563642b07181166fcbeab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736789"
---
# <a name="export-and-import-dqs-knowledge-bases-using-dqsinstallerexe"></a><span data-ttu-id="7074f-102">Export and Import DQS Knowledge Bases Using DQSInstaller.exe</span><span class="sxs-lookup"><span data-stu-id="7074f-102">Export and Import DQS Knowledge Bases Using DQSInstaller.exe</span></span>
  <span data-ttu-id="7074f-103">기존 DQS 설치의 경우 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 의 모든 기술 자료를 한 번에 DQS 백업 파일(.dqsb)로 내보낸 다음 나중에 명령 프롬프트에서 DQSInstaller.exe 파일을 실행하여 .dqsb 파일을 통해 다른 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 로 모든 기술 자료를 한 번에 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-103">For an existing installation of DQS, you can export all the knowledge bases in your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb) at once, and then later use the .dqsb file to import all the knowledge bases to a different [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="7074f-104">명령 프롬프트에서 DQSInstaller.exe를 실행하는 방법은 [명령 프롬프트에서 DQSInstaller.exe 실행](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#CommandPrompt)에서 [DQSInstaller.exe를 실행하여 Data Quality 서버 설치 완료](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7074f-104">For more information about running DQSInstaller.exe from the command prompt, see [Run DQSInstaller.exe from Command Prompt](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#CommandPrompt) in [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
 <span data-ttu-id="7074f-105">이 기능을 사용하면 *를 사용하여 각 기술 자료를 .dqs 파일로 개별적으로 내보낼 필요 없이* 의 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 모든 [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]기술 자료를 한 번에 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-105">This feature enables you to take a backup of *all* your knowledge bases in [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once without having to individually export each knowledge base to a .dqs file by using [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="7074f-106">마찬가지로 *를 사용하여 .dqs 파일에서 각 기술 자료를 개별적으로 가져올 필요 없이 백업 파일에서 다른* 로 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 모든 [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]기술 자료를 한 번에 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-106">Similarly, you can import *all* the knowledge bases from the backup file into another [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once without having to individually import each knowledge base from a .dqs file by using [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="7074f-107">이 기능은 컴퓨터에서 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 를 제거한 다음 다른 컴퓨터에 다시 설치할 때 기술 자료를 백업 및 복원하는 데 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-107">This is particularly useful for backing up and restoring your knowledge bases when you are uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] on a computer, and then reinstalling it on a different computer.</span></span> <span data-ttu-id="7074f-108">기존 설치된 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 의 모든 기술 자료를 DQS 백업 파일(.dqsb)로 내보낸 다음 다른 컴퓨터에 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 를 설치한 후 백업 파일에서 모든 기술 자료를 손쉽게 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-108">You can easily export all the knowledge bases in an existing installation of [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb), and then import all the knowledge bases from the backup file after installing [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] on a different computer.</span></span>  
  
##  <a name="exporting-knowledge-bases-to-dqsb-file"></a><a name="export"></a> <span data-ttu-id="7074f-109">.dqsb 파일로 기술 자료 내보내기</span><span class="sxs-lookup"><span data-stu-id="7074f-109">Exporting Knowledge Bases to .dqsb File</span></span>  
 <span data-ttu-id="7074f-110">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 를 제거하는 동안을 비롯하여 언제든지 기존 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]의 모든 기술 자료를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-110">You can export all the knowledge bases in the existing [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at any time or while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].</span></span>  
  
-   <span data-ttu-id="7074f-111">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 의 모든 기술 자료를 DQS 백업 파일(.dqsb)로 내보내려면 기술 자료를 내보낼 전체 경로 및 파일 이름과 함께 명령 프롬프트에서 `exportkbs` 매개 변수를 사용하여 DQSInstaller.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-111">To export all the knowledge bases in a [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb), run DQSInstaller.exe with the `exportkbs` parameter from the command prompt, along with the full path and file name where you want to export the knowledge bases.</span></span> <span data-ttu-id="7074f-112">예를 들어 C: 드라이브의 DQSBackup.dqsb 파일로 모든 기술 자료를 내보내려면:</span><span class="sxs-lookup"><span data-stu-id="7074f-112">For example, to export all the knowledge bases to the DQSBackup.dqsb file in the C: drive:</span></span>  
  
    ```  
    dqsinstaller.exe -exportkbs c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="7074f-113">지정된 파일 이름이 지정된 위치에 이미 있는 경우 설치 관리자에서 파일을 덮어쓸지 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-113">If the provided file name already exists at the specified location, the installer prompts you whether to overwrite the file.</span></span>  
  
-   <span data-ttu-id="7074f-114">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]를 제거하는 동안 모든 기술 자료를 DQS 백업 파일로 내보내려면 기술 자료를 내보낼 전체 경로 및 파일 이름과 함께 명령 프롬프트에서 `uninstall` 매개 변수를 사용하여 DQSInstaller.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-114">To export all the knowledge bases to a DQS backup file while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], run DQSInstaller.exe with the `uninstall` parameter from the command prompt, along with the full path and file name where you want to export the knowledge bases.</span></span> <span data-ttu-id="7074f-115">예를 들어 C: 드라이브의 DQSBackup.dqsb 파일로 모든 기술 자료를 내보내고 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]의 설치를 해제하려면:</span><span class="sxs-lookup"><span data-stu-id="7074f-115">For example, to export all the knowledge bases to the DQSBackup.dqsb file in the C: drive, and then uninstall [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]:</span></span>  
  
    ```  
    dqsinstaller.exe -uninstall c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="7074f-116">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 매개 변수를 사용하여 명령 프롬프트에서 `uninstall` 를 제거하는 동안 DQS 백업 파일의 전체 경로 및 파일 이름을 지정하지 않은 경우 모든 기술 자료가 삭제됨을 알리고 제거 프로세스를 계속할지 여부를 선택하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-116">If you do not specify the full path and file name of the DQS backup file while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] from the command prompt using the `uninstall` parameter, a message is displayed stating that all the knowledge bases will be deleted, and allows you to choose whether to continue with the uninstall process.</span></span>  
  
##  <a name="importing-knowledge-bases-from-dqsb-file"></a><a name="import"></a> <span data-ttu-id="7074f-117">.dqsb 파일에서 기술 자료 가져오기</span><span class="sxs-lookup"><span data-stu-id="7074f-117">Importing Knowledge Bases from .dqsb File</span></span>  
 <span data-ttu-id="7074f-118">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 설치를 완료한 후 DQS 백업 파일(.dqsb)에서 모든 기술 자료를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-118">You can import all the knowledge bases from a DQS backup file (.dqsb) after completing the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation.</span></span> <span data-ttu-id="7074f-119">기술 자료를 가져오려면 유효한 DQS 백업 파일(.dqsb)이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-119">To import knowledge bases, you must have a valid DQS backup file (.dqsb).</span></span>  
  
 <span data-ttu-id="7074f-120">기술 자료를 가져올 전체 경로 및 파일 이름과 함께 명령 프롬프트에서 `importkbs` 매개 변수를 사용하여 DQSInstaller.exe 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-120">Run the DQSInstaller.exe file with the `importkbs` parameter from the command prompt, along with the full path and file name from where you want to import the knowledge bases.</span></span> <span data-ttu-id="7074f-121">예를 들어 C: 드라이브의 DQSBackup.dqsb 파일에서 모든 기술 자료를 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="7074f-121">For example, to import all the knowledge bases from the DQSBackup.dqsb file in the C: drive:</span></span>  
  
```  
dqsinstaller.exe -importkbs c:\DQSBackup.dqsb  
```  
  
 <span data-ttu-id="7074f-122">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 에 가져오려는 기술 자료와 이름이 같은 기술 자료가 이미 있는 경우 가져온 기술 자료의 이름에 밑줄(_)과 함께 1부터 시작되는 정수 값이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-122">If there are existing knowledge bases in your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] with the same name as the ones you are importing, the names of the imported knowledge bases will be appended with an underscore (_) followed by an integer value starting with 1.</span></span> <span data-ttu-id="7074f-123">예를 들어 "CompanyName" 도메인이 중복된 경우 가져온 도메인 이름은 "CompanyName_1"이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7074f-123">For example, if the "CompanyName" domain is duplicate, the imported domain name will be "CompanyName_1."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7074f-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7074f-124">See Also</span></span>  
 <span data-ttu-id="7074f-125">[DQSInstaller.exe를 실행 하 여 Data Quality 서버 설치 완료](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="7074f-125">[Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md) </span></span>  
 <span data-ttu-id="7074f-126">[Data Quality Services 설치](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="7074f-126">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 <span data-ttu-id="7074f-127">[기술 자료를 dqs 파일로 내보내기](../export-a-knowledge-base-to-a-dqs-file.md) </span><span class="sxs-lookup"><span data-stu-id="7074f-127">[Export a Knowledge Base to a .dqs File](../export-a-knowledge-base-to-a-dqs-file.md) </span></span>  
 [<span data-ttu-id="7074f-128">.dqs 파일에서 기술 자료 가져오기</span><span class="sxs-lookup"><span data-stu-id="7074f-128">Import a Knowledge Base from a .dqs File</span></span>](../import-a-knowledge-base-from-a-dqs-file.md)  
  
  
