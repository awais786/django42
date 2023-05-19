import requests
import time
from bs4 import BeautifulSoup

names = ['code-annotations', 'django-pyfs', 'django-splash', 'edx-auth-backends', 'edx-bulk-grades', 'edx-celeryutils',
         'edx-completion', 'edx-django-sites-extensions', 'edx-drf-extensions', 'edx-enterprise', 'edx-opaque-keys',
         'edx-organizations', 'edx-proctoring', 'edx-rbac', 'edx-when', 'edxval', 'event-tracking', 'super-csv',
         'django-user-tasks', 'xblock-sdk', 'edx-event-routing-backends', 'web-fragments', 'lti-consumer-xblock',
         'edx-django-release-util', 'edx-submissions', 'edx-ora2', 'help-tokens', 'edx-toggles', 'edx-search',
         'edx-enterprise-data', 'edx-django-utils', 'django-lang-pref-middleware', 'edx-i18n-tools',
         'staff-graded-xblock', 'enmerkar-underscore', 'edx-milestones', 'django-config-models', 'xblock-utils',
         'edx-ace', 'edx_credentials_themes', 'edx-ccx-keys', 'edx-analytics-data-api-client', 'edx-rest-api-client',
         'edx-tincan-py35', 'edx-ecommerce-worker', 'edx-user-state-client', 'crowdsourcehinter-xblock',
         'recommender-xblock', 'xblock-drag-and-drop-v2', 'xblock-google-drive', 'edx-api-doc-tools', 'xss-utils',
         'xblock', 'repo-tools-data-schema.git', 'done-xblock', 'django-wiki', 'schoolyourself-xblock', 'ConceptXBlock',
         'AudioXBlock', 'AnimationXBlock', 'ubcpi', 'edx-zoom', 'xblock-qualtrics-survey', 'xblock-in-video-quiz',
         'xblock-submit-and-compare', 'xblock-free-text-response', 'xblock-sql-grader', 'xblock-image-modal',
         'platform-plugin-coaching', 'acclaimbadge-xblock', 'platform-plugin-braze', 'rate-xblock', 'newrelic',
         'django-cors-headers', 'django-countries', 'django-crispy-forms', 'django-debug-toolbar', 'django-extensions',
         'django-extra-views', 'django-fernet-fields', 'django-guardian', 'django-libsass', 'django-method-override',
         'django-modelcluster', 'django-mptt', 'django-mysql', 'django-oauth-toolkit', 'django-object-actions',
         'django-oscar', 'django-phonenumber-field', 'django-pipeline', 'django-sekizai', 'django-ses',
         'django-simple-history', 'django-tables2', 'django-treebeard', 'django-waffle', 'djangorestframework',
         'djangorestframework-csv', 'drf-jwt', 'factory-boy', 'newrelic', 'pylint-django', 'pytest-django', 'rules',
         'social-auth-app-django', 'wagtail', 'djangorestframework-datatables', 'django-rest-swagger', 'rest_condition',
         'Django-contrib-comments', 'django-taggit', 'django-autocomplete-light', 'django-environ', 'django-environ-2',
         'Django-braces', 'django-elasticsearch-dsl-drf', 'sorl-thumbnail', 'django-dynamic-fixture', 'django-hijack',
         'django-fsm', 'enmerkar', 'django-filter', 'djangorestframework-xml', 'django-statici18n',
         'django-cache-memoize', 'django-parler', 'django-model-utils', 'django-choices', 'django-threadlocals',
         'django-crum', 'drf-yasg', 'django-taggit-autosuggest', 'django-classy-tags', 'django-celery-beat',
         'django-ratelimit', 'jsonfield', 'django-elasticsearch-debug-toolbar', 'drf-extensions', 'django-storages',
         'django-appconf', 'django-storage-swift', 'jasmine-core', 'algoliasearch-django', 'django-js-asset',
         'drf-flex-field', 'django-bootstrap3', 'django-webtest', 'pinax-announcements', 'django-nine',
         'django-compressor', 'django-webpack-loader', 'django-elasticsearch-dsl', 'django-datetime-widget', 'authlib',
         'django-haystack', 'django-dry-rest-permissions', 'django-multi-email-field', 'django-celery-results',
         'django-sortedm2m', 'django-stdimage', 'drf-nested-routers', 'whitenoise', 'django-soapbox', 'django-require',
         'django-widget-tweaks', 'edx-jsme', 'edx-proctoring-proctortrack', 'edx-sga', 'xblock-poll',
         'django-dynamic-filenames', 'django-braces', 'mock-django', 'django-rest-framework-xml', 'django-ipware',
         'django-contrib-comments', 'django-solo', 'django-timezone-field', 'rest-condition', 'drf-haystack',
         'xblock-problem-builder', 'xblock-vectordraw', 'xblock-activetable', 'labxchange-xblocks', 'lx-pathway-plugin'
]

def get_django_versions():
    invalid_names = []
    final_versions = {}
    for name in names:
        url = f"https://pypi.org/project/{name}/"
        response = requests.get(url)
        if response.status_code == 200:
            try:
                soup = BeautifulSoup(response.text, 'html.parser')
                classifiers_element = soup.find('ul', {'class': 'sidebar-section__classifiers'})
                if classifiers_element:
                    classifiers = [li.text for li in classifiers_element.find_all('li')]
                    for classifier in classifiers:
                        if classifier.strip().startswith("Framework"):
                            final_versions[name] = [
                                version.strip()[10:] for version in classifier.split("\n")
                                if version.strip().startswith("Django :: 4.2")
                            ]
                            break
                else:
                    invalid_names.append(name)
            except:
                print(name)

        else:
            invalid_names.append(name)

        time.sleep(0.2)

    print(f"valid names {final_versions}")
    print("-----------------")
    print(f"invalid names {invalid_names}")

if __name__ == "__main__":
    get_django_versions()
